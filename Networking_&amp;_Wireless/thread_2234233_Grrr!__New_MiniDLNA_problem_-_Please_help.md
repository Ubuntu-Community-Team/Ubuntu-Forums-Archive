---
title: "Grrr!  New MiniDLNA problem - Please help?"
date: 2014-07-13
forum: Networking &amp; Wireless
---

### Post by AnotherKevin on 2014-07-13
I installed MiniDLNA in order to stream movies and music over our families WiFi.  I'm running Kubuntu 14.04 (KDE's most recent stable)  After a little work, I got the movies going great!  Was very easy.  But, I cannot view or stream the music at all.  

Here's my MiniDLNA.conf: ```


#This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.


# Specify the user name or uid to run as.
#user=minidlna




# Path to the directory you want scanned for media files.
#
# This option can be specified more than once if you want multiple directories
# scanned.
#
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
#   media_dir=/var/lib/minidlna
media_dir=A,/home/kevin/Music    
media_dir=P,/home/kevin/Pictures
media_dir=V,/home/kevin/Videos


# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna


# Path to the directory that should hold the log file.
log_dir=/var/log


# Type and minimum level of importance of messages to be logged.
#
# The types are "artwork", "database", "general", "http", "inotify",
# "metadata", "scanner", "ssdp" and "tivo".
#
# The levels are "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
#
# The types are comma-separated, followed by an equal sign ("="), followed by a
# level that applies to the preceding types. This can be repeated, separating
# each of these constructs with a comma.
#
# The default is to log all types of messages at the "warn" level.
#log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn


# Use a different container as the root of the directory tree presented to
# clients. The possible values are:
#   * "." - standard container
#   * "B" - "Browse Directory"
#   * "M" - "Music"
#   * "P" - "Pictures"
#   * "V" - "Video"
# If you specify "B" and the client device is audio-only then "Music/Folders"
# will be used as root.
#root_container=.B


# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=eth0


# IPv4 address to listen on (e.g. 192.0.2.1/24).
# If omitted, the mask defaults to 24. The IPs are added to those determined
# from the network_interface option above.
# This option can be specified more than once.
#listening_ip=


# Port number for HTTP traffic (descriptions, SOAP, media transfer).
# This option is mandatory (or it must be specified on the command-line using
# "-p").
port=8200


# URL presented to clients (e.g. http://example.com:80).
#presentation_url=/


# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
friendly_name=Kevin's Media


# Serial number the server reports to clients.
# Defaults to 00000000.
serial=681019810597110


# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)


# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=


# Automatic discovery of new files in the media_dir directory.
inotify=no


# List of file names to look for when searching for album art.
# Names should be delimited with a forward slash ("/").
# This option can be specified more than once.
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg
album_art_names=AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg
album_art_names=Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg


# Strictly adhere to DLNA standards.
# This allows server-side downscaling of very large JPEG images, which may
# decrease JPEG serving performance on (at least) Sony DLNA products.
#strict_dlna=no


# Support for streaming .jpg and .mp3 files to a TiVo supporting HMO.
#enable_tivo=no


# Notify interval, in seconds.
#notify_interval=895


# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```

My music is all in my music directory as natively set up by Ubuntu.  I use KDE.  The directory structure for my music, from the top down is Music >> Artist >> Album >> Songs.  No Genres (to my knowledge).

In the above conf file, if you see some odd stuff that's #'d out, it was just my lame attempt at fixing the problems...  This conf file is the current version.

None of the devices, nor their apps can see this directory.  Can any one help?  Even a point in the right direction would help.  None of the AskUbuntu or Ubuntu Wiki stuff has been of any help.  Tried Google, to no avail...

Kevin

---

### Post by praseodym on 2014-07-13
```
#network_interface=eth0
```
Uncomment this line, check which is the right interface name

---

### Post by AnotherKevin on 2014-07-13
> **praseodym said:**
> ```
#network_interface=eth0
```
Uncomment this line, check which is the right interface name

Eth0 is correct.  When I uncomment, the PC no longer shows on the network at all.

Kevin

---

### Post by SeijiSensei on 2014-07-14
What are the permissions on /home/kevin/Music?  By default minidlna runs with the permissions of the "minidlna" user.  To let that user see all the files in /home/kevin/Music, you need to do:
```

sudo chmod 755 /home/kevin
cd /home/kevin
chmod 755 Music
chmod -R o+rx Music/*

```
That lets all users list the contents of /home/kevin and /home/kevin/Music and makes all the files and folders under Music world-readable.

I've since installed a copy of minidlna after recommending it to you! I suggest editing /etc/default/minidlna, and making this change at the bottom:
```

# Additional options that are passed to the daemon
DAEMON_OPTS="-v"

```
Then restart the server with "sudo service minidlna restart."  That puts the server daemon into "verbose" mode and provides more extensive logging in /var/log/minidlna.log.  Maybe you'll see the answer there.

---

### Post by AnotherKevin on 2014-07-14
> **SeijiSensei said:**
> What are the permissions on /home/kevin/Music?  By default minidlna runs with the permissions of the "minidlna" user.  To let that user see all the files in /home/kevin/Music, you need to do:
```

sudo chmod 755 /home/kevin
cd /home/kevin
chmod 755 Music
chmod -R o+rx Music/*

```
That lets all users list the contents of /home/kevin and /home/kevin/Music and makes all the files and folders under Music world-readable.

I've since installed a copy of minidlna after recommending it to you! I suggest editing /etc/default/minidlna, and making this change at the bottom:
```

# Additional options that are passed to the daemon
DAEMON_OPTS="-v"

```
Then restart the server with "sudo service minidlna restart."  That puts the server daemon into "verbose" mode and provides more extensive logging in /var/log/minidlna.log.  Maybe you'll see the answer there.

Thanks, again, SeijiSensei!  That did the trick...  Should've figured it out for myself.  Your time and help is highly appreciated!

Kevin

---

