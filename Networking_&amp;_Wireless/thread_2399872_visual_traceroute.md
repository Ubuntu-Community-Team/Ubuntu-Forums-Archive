---
title: "visual traceroute"
date: 2018-08-30
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2018-08-30
I'm trying to install:
[https://visualtraceroute.net/](https://visualtraceroute.net/)
on lubuntu.

Is there a graphical traceroute in the repo?

The problem is:
$ sudo dpkg -i ovtr_1.7.1-1_amd64.deb
Selecting previously unselected package ovtr.
(Reading database ... 221281 files and directories currently installed.)
Preparing to unpack ovtr_1.7.1-1_amd64.deb ...
Unpacking ovtr (1.7.1-1) ...
dpkg: dependency problems prevent configuration of ovtr:
 ovtr depends on gksu; however:
  Package gksu is not installed.

dpkg: error processing package ovtr (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 ovtr

$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gksu' has no installation candidate

I don't know if it'll even work with the java the comes with the OS.

---

### Post by isopropanol on 2018-10-11
bump.

From what I've found gksu has been deprecated.  I don't know if there's a way to associate the command with a substitute equivalent command.
I was looking for some other alternative visual trace route and they're all old and unmaintained.  I don't know why.
Ex:
[https://github.com/cmichi/visual-traceroute](https://github.com/cmichi/visual-traceroute)
says it requires **dig **which is also saying "E: Unable to locate package dig".  Though I'll try following this rabbit hole farther.
Edit: dig is installed, so I'm not sure why apt-get says it can't find it rather than "already installed".
  But trying to run it gives me error **java.lang.ClassNotFoundException: processing.core.PApplet**
  The link to download the GeoIP list is also dead.  But I found this [https://www.maxmind.com/en/geoip-demo](https://www.maxmind.com/en/geoip-demo) and I think the DB is from [https://dev.maxmind.com/geoip/geoip2/geolite2/](https://dev.maxmind.com/geoip/geoip2/geolite2/) now.

[http://www.caida.org/tools/visualization/gtrace/](http://www.caida.org/tools/visualization/gtrace/)
complained about my 64 bit system being unrecognized.  It's from 1999.

There is an online page you paste your traceroute into [https://stefansundin.github.io/traceroute-mapper/](https://stefansundin.github.io/traceroute-mapper/) , but it doesn't look like it's working right.

And a few that trace from their server (which doesn't do what I want - I want to know my path.  That does show you where the server is if that's what you want.)
Ex: 
[https://www.monitis.com/traceroute/](https://www.monitis.com/traceroute/) 
[URL="https://gsuite.tools/traceroute"]https://gsuite.tools/traceroute


[/URL]The closest thing I can find that works is GeoIPLookup:
# get the CLI (command line) trace route tool
sudo apt-get install traceroute
# get Geo IP Lookup
[COLOR=#000000][FONT=Arial]sudo apt-get install geoip-bin
# this will only tell you the country by default[COLOR=#000000][FONT=Arial]
# example usage:[/FONT][/COLOR]
# geoiplookup 80.60.233.195[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]cd /usr/share/GeoIP
# get the latest GeoIP database[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo wget [http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz](http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo gunzip GeoIP.dat.gz
# get a finer-grained city GeoIP database[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo wget [http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz](http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo gunzip GeoLiteCity.dat.gz
# example usage:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# geoiplookup -f /usr/share/GeoIP/GeoLiteCity.dat 216.58.197.78

So now you can run a traceroute then plug the IPs into the city lookup.  Part of the output is longitude, latitude coordinates.  You can plug those into google maps to see where it is, even if geoiplookup doesn't list the city.
Tedious and manual, but it's better than nothing.
[/FONT][/COLOR]

---

### Post by him610 on 2018-10-13
> gksu has been deprecated

LTS 16.04 Synaptic Package Manager  still shows *gksu* as being available.

---

