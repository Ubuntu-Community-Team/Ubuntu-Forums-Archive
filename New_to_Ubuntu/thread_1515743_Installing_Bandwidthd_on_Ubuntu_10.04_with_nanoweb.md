---
title: "Installing Bandwidthd on Ubuntu 10.04 with nanoweb"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by lvieirabr on 2010-06-22
I am trying to install several softwares like Uniconvertor and others that failed becouse of bandwidthd. I never could install Bandwidthd.
May be becouse it was necessary to have apache and my ubuntu came with Nanoweb.
Any suggestion?
Here are the log of the bandwidthd installation:
By the way, if I try to remove the partially installed bandwidthd, it fails to.
root@luiz-laptop:/home/luiz# apt-get install bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libqimageblitz4 libkscreensaver5 libsolidcontrolifaces4
  plasma-widgets-workspace libplasma-geolocation-interface4 libksgrd4
  kdebase-workspace-bin libkworkspace4 libplasmagenericshell4 libkfontinst4
  libkephal4 kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 0B/74.8kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
(Reading database ... 179172 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@luiz-laptop:/home/luiz# 

By the way, if I try to remove the partially installed bandwidthd, it  fails to:
root@luiz-laptop:/home/luiz# dpkg --remove --force-remove-reinstreq bandwidthd
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 179171 files and directories currently installed.)
Removing bandwidthd ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing bandwidthd (--remove):
 subprocess installed pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bandwidthd

---

