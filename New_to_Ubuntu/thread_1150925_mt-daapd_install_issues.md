---
title: "mt-daapd install issues"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by baddnady23 on 2009-05-06
When trying to install mt-daapd, this is the problem that I have been getting vie the terminal:
> 
andrew@andrew-desktop:~$ sudo apt-get install mt-daapd
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mt-daapd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mt-daapd (0.9~r1696.dfsg-9) ...
Starting mt-daapd: invoke-rc.d: initscript mt-daapd, action "start" failed.
dpkg: error processing mt-daapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mt-daapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have any ideas?  I had removed it to reinstall it after having problems accessing it after updating to 9.04

---

### Post by mick8985 on 2009-05-06
first of all find out what the error is try this, and paste what it says.
```
sudo dpkg --configure mt-daapd
```

---

### Post by baddnady23 on 2009-05-06
> andrew@andrew-desktop:~$ sudo dpkg --configure mt-daapd
[sudo] password for andrew: 
Setting up mt-daapd (0.9~r1696.dfsg-9) ...
Starting mt-daapd: invoke-rc.d: initscript mt-daapd, action "start" failed.
dpkg: error processing mt-daapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mt-daapd
andrew@andrew-desktop:~$ 



thanks

---

### Post by mick8985 on 2009-05-06
Hmm perhaps the old initscript wasn't remove when you uninstalled, and is not compatible with the new version try.

```
sudo /etc/init.d/mt-daapd start
```

---

### Post by baddnady23 on 2009-05-06
> andrew@andrew-desktop:~$ sudo /etc/init.d/mt-daapd start
Starting mt-daapd: andrew@andrew-desktop:~$ 

This is what i get as a resault of your last post.

---

### Post by mick8985 on 2009-05-06
uninstall mt-daapd and see if the /etc/init.d/mt-daapd file still exists.
If it does, delete it then reinstall.

---

### Post by baddnady23 on 2009-05-06
Ok i think i may be getting somewhere now it is just saying that i need the mt-daapd.conf file..


> andrew@andrew-desktop:~$ sudo mt-daapd -f
Error opening config file: No such file or directory
Error reading config file (/etc/mt-daapd.conf)
andrew@andrew-desktop:~$ 

---

### Post by mick8985 on 2009-05-06
```
# $Id: mt-daapd.conf.templ 1660 2007-09-12 13:08:04Z rpedde $
#
# This is the mt-daapd config file.
#
# If you have problems or questions with the format of this file,
# direct your questions to rpedde@users.sourceforge.net.
#
# Questions and discussions about the format and content of this
# config file can probably be obtained by consulting the wiki:
#
# http://wiki.fireflymediaserver.org/Config_File
#
# Or by asking questions on the forums at
#
# http://forums.fireflymediaserver.org
#
#

[general]

#
# web_root (required)
#
# Location of the admin web pages.
#
# If you installed from .RPM, .deb, or tarball with --prefix=/usr, then
# this is correct. 
#
# If you installed from tarball without --prefix=/usr, then the correct
# path is probably /usr/local/share/mt-daapd/admin-root.
#

web_root = /usr/share/mt-daapd/admin-root

#
# port (required)
#
# What port to listen on.  It is possible to use a different
# port, but this is the default iTunes port
#

port = 3689

#
# admin_pw (required)
#
# This is the password to the administrative pages
#

admin_pw = mt-daapd


#
# db_type (required)
#
# This is what kind of backend database to store the song
# info in.  Valid choices are "sqlite" and "sqlite3".
#

db_type = sqlite3

#
# db_parms
#
# This is any extra information the db needs to connect.
# in the case of sqlite and sqlite3, this is the name
# of the directory to store the database in
#
# If you installed from RPM or .deb, this path likely already
# exists.  If not, then you must create it.  The directory itself
# must be writable by the "runas" user.
#

db_parms = /var/cache/mt-daapd

#
# mp3_dir (required)
#
# Location of the mp3 files to share.  Note that because the
# files are stored in the database by inode, these must be
# in the same physical filesystem.
#

mp3_dir = /home/media/music

#
# servername (required)
#
# This is both the name of the server as advertised
# via rendezvous, and the name of the database
# exported via DAAP.  Also know as "What shows up in iTunes".
#

servername = Firefly %v on %h

#
# runas (required)
#
# This is the user to drop privs to if running as
# root.  If mt-daapd is not started as root, this
# configuration option is ignored.  Notice that this
# must be specified whether the server is running
# as root or not.
#
# This is also ignored on Windows.
#

runas = mt-daapd

#
# password (optional)
#
# This is the password required to listen to MP3 files
# i.e. the password that iTunes prompts for
#

#password = mp3

#
# extensions (optional)
#
# These are the file extensions that the daap server will
# try to index and serve.  By default, it only indexes and
# serves .mp3 files.  It can also server .m4a and .m4p files,
# and just about any other files, really.  Unfortunately, while
# it can *attempt* to serve other files (.ogg?), iTunes won't
# play them.  Perhaps this would be useful on Linux with
# Rhythmbox, once it understands daap.  (hurry up!)
#
# Failing that, one can use server-side conversion to transcode
# non-standard (.ogg, .flac) music to wav on the server side.
# See the ssc_* options below.
#
# To be able to index .ogg files, you'll need to have configured
# with --enable-oggvorbis.  For .flac, --enable-flac, for .mpc,
# --enable-musepack.
#

extensions = .mp3,.m4a,.m4p,.ogg,.flac,.mpc

#
# ssc_codectypes (optional)
#
# List of codectypes for files that the daap server should
# perform internal format conversion and present to clients
# as WAV files.  The file extensions that these codectypes correspond
# to must also be present in 'extensions'
# configuration value, or files are not probed in the first
# place.
#
# Valid codectypes:
#
# mp4a - for AAC (.aac, .mp4, .m4a, .m4p)
# mpeg - for mp3
# wav - for wav
# wma - for wma
# ogg - for ogg
# flac - for flac (.flac, .fla)
# mpc for musepack (.mpc, .mpp, .mp+)
# alac for alac (.m4a)
#

# Not needed because ffmpeg is enabled (all file types transcoded to wav.
# If this behavior is undesired, see the [plugins] section and disable it,
# or selectively disable codecs below with the never_transcode option.)
# -joshk
# ssc_codectypes = ogg,flac,alac

# never_transcode (optional)
# Comma separated list of formats to never transcode. (Nothing by default)
# never_transcode = ogg

#
# ssc_prog (optional)
#
# Program that is used in server side format conversion.
# Program must accept following command line syntax:
#     ssc_prog filename offset length ...
# Parameter filename is the real name of the file that is
# to be converted and streamed, offset is number of bytes
# that are skipped from the beginning of the _output_ file
# before streaming is started, length is length of the song
# in seconds (or zero).  All other possible arguments must
# be ignored.  The resulting wav file (or the rest of
# the file after initial seek) is written to the standard
# output by the ssc_prog program.  This is typically
# a script that is a front end for different conversion tools
# handling different formats.
#

# ssc_prog = /usr/bin/mt-daapd-ssc.sh

#
# logfile (optional)
#
# This is the file to log to.  If this is not configured,
# then it will log to the syslog.
#
# Not that the -d <level> switch will control the log verbosity.
# By default, it runs at log level 1.  Log level 9 will churn
# out scads of useless debugging information.  Values in between
# will vary the amount of logging you get. However, you must log
# to a file to see this debugging information (debug information will
# not appear in syslog.)
#

#logfile = /var/log/mt-daapd.log

#
# rescan_interval
#
# How often to check the file system to see if any mp3 files
# have been added or removed. 
#
# if not specified, the default is 0, which disables background scanning.
#
# If background rescanning is disabled, a scan can still be forced from the 
# "status" page of the administrative web interface
#
# Setting a rescan_interval lower than the time it takes to rescan
# won't hurt anything, it will just waste CPU, and make connect times
# to the daap server longer.
#
#

#rescan_interval = 300

# always_scan 
#
# The default behavior is not not do background rescans of the
# filesystem unless there are clients connected.  The thought is to
# allow the drives to spin down unless they are in use.  This might be
# of more importance in IDE drives that aren't designed to be run
# 24x7.  Forcing a scan through the web interface will always work
# though, even if no users are connected.

# always_scan = 0

#
# scan_type
# 
#
# This sets how aggressively mp3 files should be scanned to determine
# file length.  There are three values:
#
# 0 (Normal) 
#   Just scan the first mp3 frame to try and calculate size.  This will
#   be accurate for most files, but VBR files without an Xing tag will
#   probably have wildly inaccurate file times.  This is the default.
#
# 1 (Aggressive)
#   This checks the bitrates of 10 frames in the middle of the song.  
#   This will still be inaccurate for VBR files without an Xing tag,
#   but they probably won't be quite as inaccurate as 0.  This takes
#   more time, obviously, although the time hit will only happen the
#   first time you scan a particular file.
#
# 2 (Painfully aggressive)
#   This walks through the entire song, counting the number of frames.
#   This should result in accurate song times, but will take the most
#   time.  Again, this will only have to be incurred the first time
#   the file is indexed.
# 

scan_type = 2

#
# compress
#
# Whether to use gzip content-encoding when transferring playlists etc.
# This was contributed as a patch by Ciamac Moallemi just prior to the 0.2.1
# release, and as such, hasn't gotten as much testing as other features.
#
# This feature should substantially speed up transfers of large databases
# and playlists.
#
# It will eventually default to 1, but currently it defaults to 0.
#

#compress = 0

[plugins]
plugin_dir = /usr/lib/mt-daapd/plugins
plugins = rsp.so,ssc-ffmpeg.so


[scanning]

# should playlists be processed at all?
#
process_playlists = 1

 
# should itunes xml files be processed?
#
process_itunes = 1

# should m3u files be processed?
#
process_m3u = 1
```

That's the default contents of the configuration file. You've had it installed before so you no doubt have tinkered with it before. Just copy and paste into
```
/etc/mt-daapd.conf
```
edit the config file then restart mt-daapd and you should be sorted.

---

### Post by baddnady23 on 2009-05-06
haha getting even closer i beleive.  Only problem now is that I can not access the settings via the brower when i put [http://localhost:3689](http://localhost:3689) in.  It just says that it failed to connect.  Thank you for all your help so far.

---

### Post by mick8985 on 2009-05-06
Hmm that's curious, I dunno what could be wrong, are you sure that the mt-daapd daemon has been executed properly and is running?

what happens if you execute it form the command line like so:

```
sudo mt-daapd -c /etc/mt-daapd.conf
```

---

### Post by baddnady23 on 2009-05-06
i get this, and still no response in the browser.

> andrew@andrew-desktop:~$ sudo mt-daapd -c /etc/mt-daapd.conf
andrew@andrew-desktop:~$ 

---

### Post by mick8985 on 2009-05-06
I'm at a loss, is it visible in rythmbox/itunes from another computer on your network?

Edit-
lol mines not working now...

---

### Post by mick8985 on 2009-05-06
I rebooted and it works again, I think all that stopping and starting the deamon might have caused something to mess up at some point. perhaps you should try the same.

---

### Post by baddnady23 on 2009-05-06
I've tried restarting lol.  no it doesn't show up in itunes or on the network anywhere else including my own rhythmbox.

---

### Post by mick8985 on 2009-05-06
Check mt-daapd is actually running with.
```
ps aux | grep mt-daapd
```
If it is running do
```
nmap localhost
```
to see which ports are in use

---

### Post by Strawp on 2009-05-21
I've been using mt-daapd for a year or two and every time I do a major upgrade or server rebuild I have problems getting it back up again.

I had the exact same output as baddnady23, got to the end of the thread thinking the service was dead to the world, ran nmap and there it is happily rendezvousing with the network :P

Basically, there seems to be some issue apt-get removing and apt-get installing mt-daapd and the way to resolve an install is to back up the config you had in /etc/mt-daapd.conf and the db in /var/cache/mt-daapd/[usually songs3.db] then apt-get remove mt-daapd and *manually* remove the script /etc/init.d/mt-daapd and whatever the location is that "whereis mt-daapd" responds to.

Once it's all gone, "apt-get install mt-daapd", making sure there's a valid config file in /etc/mt-daapd.conf and starting the daemon with sudo "mt-daapd -c /etc/mt-daapd.conf" seems to do the trick.

---

