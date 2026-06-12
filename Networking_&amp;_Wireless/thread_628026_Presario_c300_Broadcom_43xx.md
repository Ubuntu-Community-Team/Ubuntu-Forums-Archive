---
title: "Presario c300 Broadcom 43xx"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by DEDb33t on 2007-11-30
hello,

Currently i am running off a presario c300 laptop with a broadcom chipset.

I have gotten wifi to work but it is mighty jenky.

Each time i restart my computer the wireless fails to work and i have to unistall the bcm43xx fwcutter reinstall the package and then install the wl_apsta-3.130.20.0.o file.

After that process the internet comes up again.

If anyone could help me create a more permanent connection that would be great.


Also as a side not the add/remove programs does not work for anytime i attempt to install something it has to "refresh" and downloads six files.

it does anytime a click the checkbox to the left of a program

anyhelp would be great thanks alot

---

### Post by mrmiserable on 2007-11-30
ndiswrapper i prefere i am not on laptop but wifi on desktop and it never fails me allways connected 

if you need help just ask

by the way im using gutsy and ndiswrapper 1.46 from source

---

### Post by DEDb33t on 2007-11-30
ok so i take it i need to set up ndiswrapper

i have 1.49 on my desktop in tar.gz format

any guidance in its usage and setting it up would be much obliged

---

### Post by mrmiserable on 2007-11-30
ok firstly ndiswrapper is on live cd also this is easiest way to install ndiswrapper

secondly you will need your wireless drivers 

do you have these if yes then

```
sudo ndiswrapper -i your driver.inf file
```

next blacklist your native drivers

sudo gedit /etc/modprobe.d/blacklist

at bottom of file just add

 blacklist bcm43xx


next 

sudo rmmod bcm43xx  (turns of native drivers )
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper 
sudo ifdown eth1 (eth1 is mine yours could be different)
sudo ifup eth1
sudo dhclient

if network manager cannot connect 
right click and enter manually your network

if you want your network to start on boot just ndiswrapper -m
or ndiswrapper -ma

any problems ask

---

### Post by DEDb33t on 2007-11-30
so i take it i need to download the ndiswrapper iso and burn it to cd if so where can i find the complete document b.c i have tar.gz files named ndiswrapper 1.49 would this be it?

i thought my driver was the wl_apsta file?
if not i do have a folder with WLANBroadcom files in it would that contain the driver?
if not i do not have any .inf files would there be a place i could download the driver on the internet?


other than that i think i understand it all


thanks for all the help

---

### Post by DEDb33t on 2007-11-30
would this be the driver i need


[http://www.x-drivers.com/catalog/drivers/wireless_networks/companies/broadcom/models/bcm4311/1844.html](http://www.x-drivers.com/catalog/drivers/wireless_networks/companies/broadcom/models/bcm4311/1844.html)

---

### Post by mrmiserable on 2007-12-01
no 
on your vista setup there is a file with a    .sys  .inf and i think .cat files (mine are WMP54GS.INF for your understanding)

copy paste this to your home folder  

you can just copy whole folder but make sure these files are in there

---

### Post by kevdog on 2007-12-01
Vista drivers dont work with ndiswrapper.  You need XP drivers.  See this thread:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by DEDb33t on 2007-12-01
ive never run off vista on this laptop or ever for that matter.

also its not partitioned so the files dont exist...

is there another place i can get them?

---

### Post by DEDb33t on 2007-12-01
bump

---

