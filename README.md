listenr
=======

CLI script to listen to internet radio

## Prerequisites

- Run on GNU/Linux platform. Not really tested on other platforms.
- Install `mplayer`: Connects to radio URL and plays the audio stream. Use `apt install mplayer` to install.
- Install `dialog`: This allows you to select from a list the stations. Use `apt install dialog` to install.
- Install `cmatrix`: This will make a nifty visualization in your terminal while playing. Use `apt install cmatrix` to install.
- PHP is required to run the streamwatch component.

## Installation

Once you clone this repository, symlink the file `listenr` into your $PATH.

There is a file called `stations.conf.example`. Copy this file to
`stations.conf`. You can add your own favorite internet radio stations to this
file to easily select them and listen to them with listenr.

Here is the format for the stations, four pieces of data per line with pipes `|` in between.

```
station_id|station_name|url|color
```
 - `station_id` is an id you make up to refer to the station (no spaces)
 - `station_name` is a name or description you can give to find the station in the list
 - `url` is the URL to the internet stream
 - `color` is a color to use for the matrix visualization. Valid colors are green, red, blue, white, yellow, cyan, magenta and black.

Example `stations.conf` file:
```
mpr-classical|MPR - Classical|http://classicalstream1.publicradio.org:80/|blue
current|The Current|http://currentstream1.publicradio.org:80/|blue
weather|Weather Radio - 55420|http://audioplayer.wunderground.com/tim273/edina|cyan
```
## Usage

```
Usage: listenr [-d] [-n] [--list] [station]
  -d Debug mode (bypass the streamwatch pipe)
  -n No matrix animation (cmatrix)
  --list List available stations from config file

Available stations are configured in stations.conf file (/path/to/file/stations.conf).
mplayer output is piped to streamwatch (included with listenr program) 
  to display desktop notifications of stream song changes.
Without a station argument a dialog will present list for selecting a station.

Example: listenr -d weather
```
