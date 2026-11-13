# NYC Charter Schools Map

An interactive map of every charter school in New York City, with **Success Academy** highlighted.

**291 charter schools at 423 locations, including 57 Success Academy locations.** I checked the data and fixed or removed 6 records (see [Data checks](#data-checks)).

**Live map:** https://willmurray98.github.io/nyc-charter-schools-map/

## What it does

- One pin per school location. Click a pin to see the school's name, address, borough, district and type.
- Search by name, address or ZIP code, and filter by borough.
- Success Academy pins are larger and orange, always visible, and can be shown on their own with a toggle.
- Other pins group into numbered clusters when zoomed out.
- Works on desktop and phone.

## Data

**Source:** [New York State Education Department charter school locations](https://gisservices.its.ny.gov/arcgis/rest/services/NYS_Schools/FeatureServer/4), downloaded November 12, 2026. The file is saved unchanged in [`data/`](data/nyc-charter-schools.geojson), and the map reads only that file.

The state lists 291 charter schools in NYC. Many have more than one campus, so there are 423 locations in all:

| Borough | Schools | Extra campuses | Locations |
| --- | --- | --- | --- |
| Manhattan | 53 | 26 | 79 |
| Bronx | 101 | 44 | 145 |
| Brooklyn | 94 | 49 | 143 |
| Queens | 35 | 12 | 47 |
| Staten Island | 8 | 1 | 9 |
| **Total** | **291** | **132** | **423** |

**Success Academy:** 57 locations on the map, plus 2 approved schools not yet open (NYC 15 and NYC 18). The state groups the 57 locations under 38 school records and lists the other 19 as extra campuses.

## Data checks

The downloaded file is untouched. These fixes are made in a short, commented block at the top of the code in `index.html`.

- **3 records left off:** Minisink Charter School is in Albany, not NYC. Success Academy NYC 15 and NYC 18 are approved but have no school building yet. The state lists them at the network's office.
- **3 pins moved:** Success Academy NYC 17 is listed at the network's office. I moved its pin to its school in Ridgewood, Queens, using the address from the [SUNY Charter Schools Institute](https://newyorkcharters.org/charter-schools/success-academy-charter-school-17). Compass Charter School and Middle Village Prep were placed far from their own addresses, so I moved them. I checked every pin against its address, and all the others are close.
- **Boroughs come from ZIP codes:** the state's county field puts 5 schools in the wrong borough.
- **Names and addresses tidied:** they are converted from ALL CAPS, and three typos in school names are fixed.

## Run it locally

Open a terminal in this folder and run the command below, then go to <http://localhost:8000>. Opening the file directly doesn't work, because browsers block it from loading the data file.

```bash
ruby -run -e httpd . -p 8000
```

## How it was built

Built with [Claude Code](https://claude.com/claude-code) in 1 hour 30 minutes: about 1 hour on the core map and 30 minutes checking and fixing the data.
