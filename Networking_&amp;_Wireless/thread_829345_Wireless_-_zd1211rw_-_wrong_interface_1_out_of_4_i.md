---
title: "Wireless - zd1211rw - wrong interface 1 out of 4 ish"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by namraw on 2008-06-14
Yet another wireless problem i have searched google ubuntufourums etc etc no luck, so i have to bight my tounge and post feels like ive lost but we'll see... ive posted the usual requested outputs and some discoveries of my own.

The problem i am having is every 3-5 restarts my wireless works and all the others it does not all the following results were taken on time it was not working with a cable trailing across the house :D.

Using: Belkin Wireless G  USB Adapter - F5D7050v4
Chipset: ZD1211
Driver in use: zd121rw

ive tried using ndiswrapper didn't work as there are no 64bit drivers for device and downgrading to 32 is a last resort ....

lshw -C network:
```
namraw@namraw-desktop:~$ lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:fa:53:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
```

iwlist eth1 scan:
```
namraw@namraw-desktop:~$ sudo iwlist eth1 scan
eth1      No scan results
```
no scan results although brother (using windows) is connected down the hall

set up from scratch for wireless
```
namraw@namraw-desktop:~$ sudo ifconfig eth1 down
[sudo] password for namraw: 
namraw@namraw-desktop:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:17:3f:fa:53:6f
Sending on   LPF/eth1/00:17:3f:fa:53:6f
Sending on   Socket/fallback
namraw@namraw-desktop:~$ sudo ifconfig eth1 up
namraw@namraw-desktop:~$ sudo iwconfig eth1 essid "Warman12"
namraw@namraw-desktop:~$ sudo iwconfig eth1 key [128bit WEP KEY]
namraw@namraw-desktop:~$ sudo iwconfig eth1 key open
namraw@namraw-desktop:~$ sudo iwconfig eth1 mode Managed
namraw@namraw-desktop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:17:3f:fa:53:6f
Sending on   LPF/eth1/00:17:3f:fa:53:6f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
so it fails to asign a dhcp

out of curosity checked boot log and wen it loaded drivers zd1211rw
```
namraw@namraw-desktop:~$ dmesg | grep zd
[   52.636264] zd1211rw 2-1.4:1.0: eth2
[   52.636283] usbcore: registered new interface driver zd1211rw
[   66.511099] zd1211rw 2-1.4:1.0: firmware version 4725
[   66.552083] zd1211rw 2-1.4:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
[   67.555939] zd1211rw 2-1.4:1.0: error ioread32(CR_REG1): -110

```
appears to be using wrong interface...

Then i saved this post as draft in text file **restarted my machine 3-4 times** lost count.....

all the above commands went through as exspected when wireless would be working:
**lshw -C network** - no change
**iwlist eth1 scan** - found my network
**set up from scratch for wireless** - dhcp was assigned
**dmesg | grep zd** - tried to load to eth1 and worked... 

...and wireless works
restart again just to check and back to square one 

**so my question is how do i make that zd1211rw loads to eth1 and eth2.....**

---

### Post by chili555 on 2008-06-14
It's a known bug, although that doesn't help us much: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227149](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227149)

Please try *sudo gedit /etc/modprobe.d/zd1211rw*. Substitute your favorite text editor, if you don't have gedit. kwrite, nano or vim will work just as well. Gedit will open an empty file. Put in a single line:```
alias eth1 zd1211rw
```Proofread, save and close gedit.

Remove your device and reinsert it. Any change in it's behavior?

---

### Post by namraw on 2008-06-15
still trying to load it into eth2 (the wrong one)

might as well ask if ne1 knows of a 64bit driver for F5D7050 v4 that would work with ndiswrapper...
i did alot of google searches and ended up extracting a few .exe but no luck just wondering if ne1 knows were to look

if there is no more luck ill probably have to go to 32 bit and try using ndiswrapper....

---

