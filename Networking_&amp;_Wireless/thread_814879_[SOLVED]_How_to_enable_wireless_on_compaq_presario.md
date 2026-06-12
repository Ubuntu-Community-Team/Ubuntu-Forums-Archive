---
title: "[SOLVED] How to enable wireless on compaq presario c700 running hardy?"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by kspncr on 2008-06-01
Hi, I have a Compaq Presario C700 running Hardy Heron and I cannot for the life of me get the wireless (broadcom) to work. Help would be very much appreciated.

---

### Post by superprash2003 on 2008-06-01
please post iwconfig output also ensure that any WLAN drivers are enabled under system->administration->Restricted Drivers Manager ( or Hardware drivers)

---

### Post by daRealScanMan on 2008-06-01
Are you sure Broadcom is the wireless?  I have a C751 and it's Atheros AR5007, if so you need Madwifi (awesome) or ndiswrapper.  Post the output of:
```
lshw -C network
```so we know what the chipset is.

---

### Post by kspncr on 2008-06-01
kyle@kyle-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:be:70:ae
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=128.208.53.66 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

I'm just throwing it out there, but I don't know what a whole lot of this means...ha

---

### Post by kspncr on 2008-06-01
When I go to hardware drivers, there is nothing there to check or uncheck. This is what I get:
kyle@kyle-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by daRealScanMan on 2008-06-04
Have you seen this thread:  [http://ubuntuforums.org/showthread.php?t=769990]("http://ubuntuforums.org/showthread.php?t=769990") 

I don't have any experience with it (I have Atheros) but it may be what you need for your wifi chipset.

---

### Post by kspncr on 2008-06-04
Finally ! it works perfectly now, thanks a bunch!

---

### Post by tadeuszk191 on 2008-06-09
Hi Friends!
Recently I bought sub AUD500 Compaq Presario c774TU with Vista Home 32 bit and Atheros AR5007 wireless card and I would like to share with you my experience installing Ubuntu Hardy on this notebook. Generally, both 64 bit and 32 bit versions of Hardy install well and work OK the only problem being the wireless connection.

1.When trying to install inside Vista with Wubi: Ubuntu 8.04_64 does not install at all, probably because my Vista is 32 bit. Ubuntu 8.04 i386 (32 bit) installs OK and works without major glitches (there is no access to drive C: from Ubuntu) but there is no way to get wireless to work, not with madwifi-ng-r2756+ar5007 or  madwifi-nr-r3366+ar5007, and not using ndiswrapper/ndisgtk + net5211.inf(ar5007eg-32-0.2.tar.gz).

2.When installing Ubuntu 8.04_64 on separate partition, double booting with Vista the combination of  ndiswrapper/ndisgtk and net5211.inf(ar5007eg-32-0.2.tar.gz) works but only in manual mode of network manager - you have to manually enable connection after each boot or swich from wired to wireless and back. The madwifi drivers do not work.

3.Installing Ubuntu 8.04 i386 gives the best results because wireless works with madwifi-ng-r2756+ar5007 very well and network manager works in automatic mode, so plugging the wired network switches to wired connection and plugging it off automatically switches over to wireless. I used the following code to make this work:

	Code:
	sudo aptitude update update
	sudo apt-get install build-essential
	wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
	tar xvf madwifi-ng-r2756+ar5007.tar.gz
	cd madwifi-ng-r2756+ar5007/
	sudo make
	sudo make install
	sudo modprobe ath_pci
	echo 'ath_pci' | sudo tee -a /etc/modules
	sudo modprobe wlan_scan_sta
	echo 'wlan_scan_sta' | tee -a /etc/modules
	sudo reboot

	After rebooting give it a bit of time to scan and find the access points around you including your own. Make sure that if you want to update your software with update manager, do it before running the above code. If you upgrade the kernel after, the wireless will be lost.
	On the other hand, there is little point of upgrading the kernel if all your hardware works good. 

4, The swich for wireless does not work and light stays red no matter if  the connection is working or not.

5.Replacing the network manager with wicd does not work properly in Hardy because the Tray does not launch and  complains about some missing dependencies, but does not specifies which are missing.

I hope that this will be helpful to those which have Presario c774tu and want to run Ubuntu Hardy. Good Luck.

---

### Post by Chxta on 2008-06-13
Hi, can anyone host the files on some other server? It looks like madwifi is down...

---

### Post by chandler on 2008-06-23
change madwifi.org to ath5k.org

---

### Post by ruchi telang on 2008-09-24
> **kspncr said:**
> When I go to hardware drivers, there is nothing there to check or uncheck. This is what I get:
kyle@kyle-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

When I go to hardware drivers, there is nothing there to check or uncheck. This is what I get:
kyle@kyle-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/QUOTE]

---

### Post by MaLek on 2009-03-16
> **chandler said:**
> change madwifi.org to ath5k.org
when i try to replace madwifi.org with ath5k.org,i download html file called ath5k.
?

---

### Post by MaLek on 2009-03-17
```
 wget wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz


```
it will work

---

