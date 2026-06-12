---
title: "Wireless not starting Automatically at Boot up"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by rochak on 2007-12-09
Hi guys,

I am running Acer Aspire 4315 with wireless card Atheros AG5007AG. My wireless was not working initially but after some toil and using ndiswrapper it is working now :) 

The trouble is it does not start automatically at boot up.

At bootup, when I type iwconfig: my Access Point shows "Not Associated". 

If I type the following commands:

sudo iwconfig wlan0 key open XXXXXXXXXX
sudo iwconfig wlan0 essid Rochak
sudo ifconfig wlan0 up

After this when I type iwconfig,  my Access Point: 00:1A:70:F3:7A:12  which is OK

After this comes the weird bit, I need to click on Network manager manual configuration, double click "Wireless Connection", ------> Roll the Configuation again to DHCP (it is already in DHCP, but I just need to select it again from the drop down) --> Click on OK. And after a couple of minutes, my  wireless starts working. 

I have ndiswrapper in /etc/modules

Any way, this process can be automated. Thanks in advance

---

### Post by Original Brownster on 2007-12-09
Hi,
I'm not a fan of the network manager it's never worked for me, for those that it does it's great!

You can put the configuration into your /etc/network/interfaces file and uninstall network-manager, this should fix your problem.

from  'man wireless'

```
DEBIAN 3.0
       In Debian 3.0 (and later) you can  configure  wireless  LAN  networking
       devices using the network configuration tool ifupdown(8).

       File : /etc/network/interfaces

       Form : wireless-<function> <value>
              wireless-essid Home
              wireless-mode Ad-Hoc

       See also :
              /etc/network/if-pre-up.d/wireless-tools
              /usr/share/doc/wireless-tools/README.Debian
```

---

### Post by rochak on 2007-12-10
This is absolutely brilliant :: works now like a charm

for whatever tis worth, here is my /etc/network/interfaces file

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-key XXXXXXXXXX
wireless-keymode open
wireless-essid Rochak

auto wlan0



Also, I din't have a need to uninstall network manager.. it connects automatically at boot up. 

Thanks a million. This rocks

---

