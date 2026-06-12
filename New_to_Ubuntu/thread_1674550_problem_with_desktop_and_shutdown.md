---
title: "problem with desktop and shutdown"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by ankit1 on 2011-01-24
subject: problem with desktop and shutdown

hello all,
 I am new to ubuntu. Last night i insatlled it on my computer. BUt have a lot of problems with desktop.
 My top panel and bottom panel is not visible on desktop. with alt+f1 i accessed the menu.
also right click is not working on desktop. and sometimes when i create a folder on desktop though file manager no folder is visible on desktop.

Also not able top connect the internet (dsl modem)


also shutdown and restart are not working properly.i have to use shutdown button of cpu to close the cpu.

I have installed ubuntu 10.04 LTS.
Could this problem is due to old pc configuration I have?
256 mb ram pentium 3 processor. my pc donot support high quality videos.

---

### Post by PunkLV on 2011-01-24
> also shutdown and restart are not working properly
There was an issue like this as I reckon
Run in terminal when your Internet connection gets fixed
```
sudo apt-get update && apt-get upgrade
```
Also, when in GRUB, in OS selection menu, select Ubuntu and press **e**, navigate to the line with **ro quiet splash** and delete **splash**, press **b** to boot. Then, probably, you will be able to see why PC does not turn off, as Ubuntu logos will not be shown this way.
> not able top connect the internet
```
sudo dhclient eth0
```
In case this fails, please post the contens of /etc/network/interfaces
> My top panel and bottom panel is not visible on desktop.
Press Alt+F2 and run
```
gnome-panel
```
or with **--replace** flag if previous method had failed.

---

### Post by ankit1 on 2011-01-24
thanks for help
problem got fixed on few restarts. all things are working nice

---

