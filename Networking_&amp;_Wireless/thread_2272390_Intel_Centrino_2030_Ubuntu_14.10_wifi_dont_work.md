---
title: "Intel Centrino 2030 Ubuntu 14.10 wifi dont work"
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by mick16 on 2015-04-06
so i think the title.....say it by itself....but just for more information...sometime after i try 15X+ time....it finaly connect to my wifi......and sometime....not.....so what wrong?

---

### Post by ricky-flammia on 2015-04-06
It could be a driver issue. Open the terminal and type ```
sudo lshw -C network
``` This will tell you what network adapter you have so that you can download the corresponding driver. If you would like me to find the required driver for you, you can post the terminal output here.

---

### Post by mick16 on 2015-04-06
> **ricky-flammia said:**
> It could be a driver issue. Open the terminal and type ```
sudo lshw -C network
``` This will tell you what network adapter you have so that you can download the corresponding driver. If you would like me to find the required driver for you, you can post the terminal output here.



so here

  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c0
       serial: d4:be:d9:7a:70:8a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.0.116 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:49 memory:c4600000-c463ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: c4
       serial: 84:a6:c8:f2:b4:f3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-33-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:c4500000-c4501fff

---

### Post by ricky-flammia on 2015-04-06
You can find the download link and installation instructions and further information for the driver that corresponds to your particular wireless device which happens to be a Centrino Wireless-N 2230 at this link. [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi) It you have any trouble installing it feel free to let me know. P.S. Ensure that Ubuntu is up to date and that all of the proper update repositories are selected first as this may serve as a solution as well.

---

### Post by wildmanne39 on 2015-04-06
The driver he needs comes installed so he would be better off trying to find out what is going on then trying to install a driver that is already installed, please click on the wireless script in my signature and follow the directions for running the script and posting the results here, I will try to follow up but I am very busy so mainly I am just pointing you in the right direction so you can get the help you need. 
Thanks

---

### Post by mick16 on 2015-04-07
[ATTACH]261160[/ATTACH]

so nope the prob still persist

---

### Post by ricky-flammia on 2015-04-07
I'll check back periodically to see if there is anything further that I can contribute to finding a solution but I'll primarily allow Wild Man take it from here.

---

### Post by wildmanne39 on 2015-04-08
First go into your router and change encryption to just wpa2 AES CCMP only.
Please copy and paste these commands for accuracy one line at a time:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
if it will not connect then do:
```
sudo sed -i '/11n_disable/ d' /etc/modprobe.d/iwlwifi.conf
```
Reboot then do:
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Does it connect?
Thanks

---

