---
title: "HowTo ?: Remove current wireless card drivers and use ndiswrapper one or madwifi"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Gohalien on 2007-04-29
I am having problems (like most of us) with wireless in Ubuntu 6.06 LTS.
I have a TP-Link W551G (Atheros chipset). It detects it fine, but signal is very low 20/94, in windows works just fine with good signal, so I wanted to use the windows xp drivers, I managed to install ndiswrapper, and I managed to install the driver, but, how I tell ubuntu to use that driver ? Thanks for your time !

---

### Post by Nonno Bassotto on 2007-04-29
First you should find what is the name of the current driver. Try
```
lsmod
```
or
```
lsmod | grep atheros
``` or something like that until you find the name of the driver you want to remove. Then remove it by
```

sudo modprobe -r NameOfTheDriver

```
To prevent the system to load it at next reboot add it to a blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
Add this line to the end of the file
```
blacklist NameOfTheDriver
```
Save and exit.

Next install ndisgtk and use the gui under System-Administration to load the Windows driver. Then you are (hopefully) done.

---

