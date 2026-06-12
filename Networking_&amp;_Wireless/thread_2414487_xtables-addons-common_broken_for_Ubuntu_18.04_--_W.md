---
title: "xtables-addons-common broken for Ubuntu 18.04 -- Workaround Wanted!"
date: 2019-03-11
forum: Networking &amp; Wireless
---

### Post by ho1ger on 2019-03-11
[COLOR=#000000][FONT=-webkit-standard]Hi all,


I am using xtables-addons-common for geofencing my Ubuntu 18.04 server.


Since January, Maxmind does not publish the IP to Location tables in the old V1 file format anymore but in a new V2 file format. The problem is that the version 3.0.0 of xtables_addons shipped with Ubuntu 18.04 cannot process the V2 files. For instance, xt_geoip_dl cannot download the new V2 files as it does not know the correct URL of the files in the new file format.


I figured that you can download xtables-addons in V 3.3 from Sourceforge ([https://sourceforge.net/projects/xtables-addons/files/](https://sourceforge.net/projects/xtables-addons/files/)).


Included in the tarball, you find new versions of xt_geoip_dl and xt_geoip_build. However, my server is somehow not able to use the converted GeoIP tables as I can see many connection attemts from countries that I actually tried to block. So I figured maybe you also need an updated kernel module xt_geoip.


So I executed the holy trinity in the downloaded tarball


./configure
make
make install


but the xt_geoip kernel module seems not to be installed correctly as it is missing when I say lsmod. I tried to modprobe xt_geoip but the system tells me:


modprobe: FATAL: Module xt_geoip not found in directory /lib/modules/4.15.0-46-generic


What am I doing wrong? Is there maybe an easier option (ppa?) that gives access to the new version of xtables_addons?


Any help is highly appreciated!


[/FONT][/COLOR]

---

### Post by sander1ub on 2019-06-13
I fixed this using module-assistant. Install it together with the xtables-addons-source:

[FONT=courier new]sudo apt-get install module-assistant xtables-addons-source[/FONT]

Then run module-assistant:

[FONT=courier new] sudo module-assistant auto-install xtables-addons-source[/FONT]

The required files will be created in */lib/modules/4.15.0-46-generic/updates/dkms*

---

