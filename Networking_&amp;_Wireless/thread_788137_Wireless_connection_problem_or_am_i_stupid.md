---
title: "Wireless connection problem or am i stupid?"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by ubergam3r on 2008-05-09
Hi, Ive just installed the latest Ubuntu Followed the doc support for setting up the wireless devices using ndiswrapper. In the windows wireless driver section i have installed the driver and it says that the hardware is present.

Now at the moment i am connected by Ethernet cable, so then i unplug it thinking great ill connect by wireless..... but i can not find anywhere to do so. I click the network manager manual config it has in connections ptp and wired but no wireless. i right click on the network manager find edit wireless networks open it and there no connections. any ideas?

---

### Post by prshah on 2008-05-09
> **ubergam3r said:**
> Hi, Ive just installed the latest Ubuntu Followed the doc support for setting up the wireless devices using ndiswrapper. In the windows wireless driver section i have installed the driver and it says that the hardware is present.


Open a terminal, and give the commands:```
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
iwconfig
```

Has your wireless adapter appeared?

---

### Post by ubergam3r on 2008-05-10
sorry for late reply, could not do above commands due to the "sudo unable to something the host" error, anyway fixed that did the commands..got

> 
tehpirate@tehpirate-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


so appears wireless isn't installed. the windows wireless driver utility mislead me...

---

### Post by Ayuthia on 2008-05-10
You might want to check in the terminal:
```
ndiswrapper -v
ndiswrapper -l 
lshw -C network
```
It will allow you to see if the version of NDISwrapper is happy, the next checks to see if the driver is fine, and the last will see if the right module is loaded.

If you see an alternate driver listed in ndiswrapper -l, you might need to check and see if that module is loaded:
```
lsmod|grep <alternate driver>
```
Replace <alternate driver> with the driver that is listed in ndiswrapper -l.  If it shows up, you will have to remove the modules and try again:
```
sudo modprobe -r <alternate driver> ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig <logical name>
iwconfig
```
The logical name should be the name of the wireless driver in lshw -C network.
```
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 00:aa:11:bb:22:CC
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,07/11/2007, 4.150. ip=192.168.15.102 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```
If you look at the example above, you will see that the logical name is wlan0.

Hope that helps and not confuse.

---

