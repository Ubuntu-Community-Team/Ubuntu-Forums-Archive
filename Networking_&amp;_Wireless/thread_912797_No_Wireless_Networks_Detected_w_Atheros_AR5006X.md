---
title: "No Wireless Networks Detected w/ Atheros AR5006X"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2008-09-07
I have a toshiba Satellite A205-S5000 and it has an Atheros AR5BXB63 (ar5006x) WiFi card built in.  When I installed Ubuntu 8.04, it loads the proprietary drivers for the WiFi card and it says that the Atheros HAL and the support for Atheros 802.1x drivers are enabled, however my computer does not detect any wireless networks.
For some reason though, when I plug in my cheap Netgear wireless USB adapter, it detects every wireless network in range with no problems, but it's not terribly fast (54mbps).  I would like to be able to use my on board Atheros card.  I've been reading tutorials on how to set up atheros wifi cards with ubuntu all day and nothing I've tried has worked yet.
I'm pretty sure it's just a matter of figuring out how to disable the proprietary drivers and install the MADWIFI driver, but I can't for the life of me figure out how.
Is there any kind of program like the hardware manager in windows for Ubuntu?  Is there any way I can view all of the hardware and drivers attached to my machine in one place?

---

### Post by Crafty Kisses on 2008-09-07
I'd like to see the results of this command:
```
lshw -C network
```

---

### Post by N00b-un-2 on 2008-09-07
ryan@Toshiba:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:36:8c:7b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.3 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
ryan@Toshiba:~$

---

### Post by sanemanmad on 2008-09-07
Hi N00b-un-2~

I had the same problem with my moms laptop (almost same model A205 i tink:) Atheros etc...

anyhow i saved the script i used to get her wireless working so take a look at it. make any changes if you feel necessary ( it is VERY basic).

Also before you do this you will need to disable the HAL from [COLOR="Red"]System > Administration > Hardware Drivers[/COLOR]

as of maybe a month or so ago these are the most stable drivers.
This is what it looks like. I am sure there will be 100's of other ways it could be done.

oh... and I would reboot after disabling the HAL and before running the script.

#! /bin/bash
sudo
echo
mkdir /etc/lib/wireless/
cd /etc/lib/wireless/
apt-get install build-essential
wget [http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)
tar xfz madwifi-ng-r3366+ar5007.tar.gz
cd madwifi-ng-r3366+ar5007
make
make install
modprobe ath_pci
reboot

---

### Post by b2020 on 2009-04-23
why can I not download the attachment?

---

