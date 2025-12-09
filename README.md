## Usage

Connect your GPS receiver

Plug in the "USB GPS" or "serial/USB adapter"

Check which COM port it uses (e.g. COM3, COM7)

Run the app

Start GPS Grid.exe (or your published single EXE)

Select connection settings

Choose Port from the dropdown (COMx)

Set Baud rate (default is 9600 – typical for many GPS modules)

Click Connect

Status indicator should turn green

Once valid $GPRMC / $GNRMC sentences are received:

UTC and Local time update

Latitude and Longitude appear

Maidenhead grid updates

UK OS Grid shows when inside Great Britain

Click Disconnect to close the serial port cleanly.

## How It Works (Short Technical Notes)

**-NMEA Parsing**

Reads serial data and buffers until \r\n

Parses $GPRMC / $GNRMC:

Time and date → combined into a DateTime (UTC)

Latitude / longitude in ddmm.mmmm / dddmm.mmmm → decimal degrees

**-Maidenhead Grid**

Converts lat/long to standard Maidenhead locator

Precision up to 6 characters (e.g. IO91wm)

**-UK OS Grid**

Transforms WGS-84 to OSGB36 using a Helmert transform

Projects to the OS National Grid (Transverse Mercator)

Formats as a two-letter 100km tile + even-digit easting/northing (8-figure by default)

## Limitations / Disclaimer

This tool is for ham radio and general location reference only.

**Do not use this application for:**

-Safety-critical navigation

-Emergency location or life-saving operations

**Some inaccuracy is expected due to:**

-GPS receiver quality

-Datum transformations (WGS-84 ↔ OSGB36)

-Rounding to 6- or 8-figure grid references

## Credits

Developed by [UHPOWERUP](https://uhpowerup.com/) (2E0UMR) with the help of AI.

NMEA, Maidenhead and OS Grid logic implemented in C# using .NET WinForms.
