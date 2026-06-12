---
title: "WPC11 Driver"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by listenhard on 2005-11-24
Hey there. I just installed the latest distro of Ubuntu, but I need a driver for my WLAN PCMCIA card. Its a Linksys WPC11. I'm not sure how to install anything in Linux, so a little help there would be nice. Thanks

---

### Post by aznboi on 2005-11-24
first off if u have an ethernet cable connection that can work on ure ubuntu machine then great itll make things easier. goto the linksys website:
```
http://www.linksys.com
```
find the driver for u card and download them. go into terminal, and type in
```
su
``` then enter ur password and press enter. this will give u root (administrator) privleges. now do:
```
apt-get install ndiswrapper-utils
```
after that is done, type:
```
cd blah
```
and replace blah with the location of the drivers. the drivers should be in a .INF format. then do:
```
ndiswrapper -i filename.inf
```
replace filename wit hthe filename of the driver.
then do this:
```
ndiswrapper -l
```
and make sure it lists ure driver with the words "hardware present" afterwards.

now do this:

```
depmod -a
```

If there is no error, continue. To load the module type
```

modprobe ndiswrapper
```

now download this:
```
http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download
```

then cd to the location where u downloaded gtk-wifi and do this:
```
dpkg -i gtkwifi-1.09.deb
```

and then right click on ure panel, select add to panel.... and under internet there should be: wirless connectivity manager click that and then some bars should be in ure panel. click on the bars, a new window opens up with available wireless connections select one and click connect.

---

