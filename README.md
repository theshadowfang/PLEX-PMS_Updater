# PMS_Updater

PMS_Updater.sh is a shell script for updating the Plex Media Server inside the TrueNAS Core Plex plugin.

This script will search the plex.tv download site for a download link and if it is newer than the currently installed version the script will download and optionaly install the new version.


## Installation

Download the PMS_Updater.sh script in your jail:

```bash
  fetch https://raw.githubusercontent.com/theshadowfang/PLEX-PMS_Updater/main/PMS_Updater.sh
```
## Usage

Run the script as root. The following options can be used:
```bash
   -l      Local file to install instead of latest from Plex.tv
   -d      download folder (default /tmp) Ignored if -l is used
   -a      Auto Update to newer version
   -f      Force Update even if version is not newer
   -r      Remove update packages older than current version
             Done before any update actions are taken.
   -v      Verbose
```
The script will auto determine if you installed plexpass or the normal version. It will authenticate using your servers authentication token, thus no more login/password required.

The script can also be called from a cronjob to check for updates on a regular schedule.


## Troubleshooting

Python temporarily broke in some Plex version, probably in 1.16.6.1559.
If you happen to be on this release, or any other that broke python, you
can manually download the next release and update:

```bash
cd /tmp
fetch https://downloads.plex.tv/plex-media-server-new/1.16.6.1592-b9d49bdb7/freebsd/PlexMediaServer-1.16.6.1592-b9d49bdb7-FreeBSD-amd64.tar.bz2
PMS_Updater.sh -l /tmp/PlexMediaServer-1.16.6.1592-b9d49bdb7-FreeBSD-amd64.tar.bz2
```
