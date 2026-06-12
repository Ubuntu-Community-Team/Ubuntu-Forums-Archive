---
title: "Cairo-dock-plugins will not install"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Bigbob22 on 2009-01-15
I have recently downloaded cairo dock. I was trying to install the plugins for cairo dock by typing ```
sudo apt-get install cairo-dock-plugins
``` in the terminal but it would not work. This is the message I got after typing the previous command:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cairo-dock-plugins-data
Suggested packages:
  rhythmbox
The following NEW packages will be installed:
  cairo-dock-plugins cairo-dock-plugins-data
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/14.2MB of archives.
After this operation, 24.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  cairo-dock-plugins-data cairo-dock-plugins
Install these packages without verification [y/N]? y
(Reading database ... 248278 files and directories currently installed.)
Unpacking cairo-dock-plugins-data (from .../cairo-dock-plugins-data_1.6.2~rc2-0ubuntu1~gilir2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/cairo-dock-plugins-data_1.6.2~rc2-0ubuntu1~gilir2_all.deb (--unpack):
 trying to overwrite `/usr/share/locale/ja/LC_MESSAGES/cd-tomboy.mo', which is also in package cairo-dock-plug-ins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking cairo-dock-plugins (from .../cairo-dock-plugins_1.6.2~rc2-0ubuntu1~gilir2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/cairo-dock-plugins_1.6.2~rc2-0ubuntu1~gilir2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/cairo-dock/libcd-rendering.so', which is also in package cairo-dock-plug-ins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/cairo-dock-plugins-data_1.6.2~rc2-0ubuntu1~gilir2_all.deb
 /var/cache/apt/archives/cairo-dock-plugins_1.6.2~rc2-0ubuntu1~gilir2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I fix this?

---

### Post by FAMUgolfer on 2009-01-15
not sure, your download may be broken but try this........uninstall everything in synaptic dealing with cairo-dock (make sure you only uninstall packages related to cairo-dock and not just cairo!).....here is link to the beta version of cairo-dock 2http://ubuntuforums.org/showthread.php?t=1039018&highlight=cairo+dock...I highly recommend it if you are using 32-bit intrepid with an nvidia card.  Install the dock first and then the plugins.  Good luck!!!

---

### Post by Bigbob22 on 2009-01-15
Thanks a lot i reinstalled and it worked fine.

---

