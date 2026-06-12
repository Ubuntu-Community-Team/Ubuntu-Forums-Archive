---
title: "End of my rope"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by mike053074 on 2007-03-19
I'm in the unfortunate group of people who have the Broadcom BCM4318 Air Force One wireless card.  I've tried every how to and tutorial I can find, with zero success.  In fact, whenever I've followed any of them,  my wireless connection has disappeared from Administration > Networking.

Any help on this would be greatly appreciated.

---

### Post by teaker1s on 2007-03-19
top tips are
1) make sure native driver is blacklisted
2)when you have driver file to install make sure all related files are in same directory(sometimes ndiswrapper needs them)
3) install driver from commandline as nsgtk graphical installer is  bug ridden-tells you driver is installed when it's not
4) don't expect the light to come on after you see driver and hardware installed
```
sudo ndiswrapper-l
```
```
sudo modprobe ndiswrapper
```
to be sure if the card is on or off```
 iwconfig
``` post output if you need help
5) just because your driver works in windows, it may be useless in linux -if it wont work then a trip to the ndiswrapper project  wiki will produce a driver known to work

as for tutorials
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318)
or the one in my signature is very good

---

### Post by mike053074 on 2007-03-19
Here is my output

```
Installed drivers:
bcmwl5          driver installed, hardware present 
```


```
lo no wireless extensions.

eth0   no wireless extensions.

sit0     no wireless extensions.
```

---

### Post by teaker1s on 2007-03-19
Also I should mention that several times I've had above-ie driver present  / hardware present no light. 
check you have blacklisted native driver, then
```
gksudo synaptic
```
search "ndiswrapper"
install "ndiswrapper-utils-1.8 (or if avaliable 1.9 instead)
**reboot**
```
sudo modprobe ndiswrapper
```
```
iwconfig
```

---

### Post by mike053074 on 2007-03-19
I have ndiswrapper 1.8 installed, but here is my output from sudo modprobe ndiswrapper
```

FATAL: Module ndiswrapper not found.
```

---

### Post by teaker1s on 2007-03-19
okay well I'm no great expert,
But it appears the ndiswrapper module isn't installed for kernel

```
sudo apt-get install module-assistant
```
```
sudo module-assistant
``` and update/select and prepare ndiswrapper -install module
reboot and
```
sudo modprobe ndiswrapper
```

---

### Post by mike053074 on 2007-03-19
I tried it, with no change.  It seems that no matter what tutorial / how to I use, I get the same result:  my wireless connection disappears from Administration > Networking.

I'm almost ready to go back to Windows :mad:

---

### Post by teaker1s on 2007-03-19
I know it's fustrating and If you have compiled latest ndiswrapper and no success, I would recommend that if the tutorials don't work-it may be time to contact the ndiswrapper team for assistance or support.

---

### Post by mike053074 on 2007-03-19
I  appreciate all of the help.  Thanks!

---

