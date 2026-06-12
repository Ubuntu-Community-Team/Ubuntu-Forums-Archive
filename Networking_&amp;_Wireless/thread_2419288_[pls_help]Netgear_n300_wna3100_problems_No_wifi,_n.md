---
title: "[pls help]Netgear n300 wna3100 problems: No wifi, ndiswrapper isssues"
date: 2019-05-19
forum: Networking &amp; Wireless
---

### Post by itsonlynox on 2019-05-19
First time using ubunto. (Ubuntu 18.04.2 LTS)

Using a netgear n300 wna3100 usb adapter but of course it doesn't show up.  I have tried to install ndiswrapper but perhaps something went wrong.  ndiswraper utils-1.9 is missing?
I'm running Ethernet through my laptop to the pc currently.

```
lsusb
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```

```
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/4.18.0-20-generic/updates/dkms/ndiswrapper.ko
version:        1.60
vermagic:       4.18.0-20-generic SMP mod_unload 

```

```
sudo apt-get install ndiswrapper-source ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ndiswrapper' instead of 'ndiswrapper-utils-1.9'
ndiswrapper-source is already the newest version (1.60-6).
ndiswrapper is already the newest version (1.60-6).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have the drivers for the netgear, I'm just lost on how to get them installed.

---

### Post by itsonlynox on 2019-05-19
anyone?

---

### Post by chili555 on 2019-05-19
ndiswrapper requires Windows ***XP*** driver files. Do you have them?

Frankly, I haven't seen ndiswrapper work correctly in many years. I suspect that there is no chance that we will get the device working.

---

### Post by itsonlynox on 2019-05-20
I do have the drivers in xp.

---

### Post by chili555 on 2019-05-20
Please open a terminal and navigate to the location of the XP inf and sys files. For example:```
cd ~/Downloads/Windows/
```Check to see if the files are actually there:```
ls
```You should see something like bcmwlhigh6.inf or similar. Install with:```
sudo ndiswrapper -i bcmwlhigh6.inf
```Of course, substitute your driver name if not bcmwlhigh6.inf. Next:```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
ndiswrapper -l
```That is a lower-case L for 'list.' It should report that the driver is installed and the device is present.

Does a new wireless device appear?```
iwconfig
```Are there any interesting messages in the log?```
dmesg | grep ndis
```

---

