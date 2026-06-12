---
title: "Broadcom Wireless for 8.10"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2008-10-30
This is a thread to help out those with Broadcom wireless issues in 8.10. Post your problems and/or solutions to get help or help out others. :) Please feel free to share anything that may help others out.

*****NOTE IT IS RECOMMENDED THAT YOU TRY AN FIND A WAY TO UPDATE 8.10 AND ALSO TRY TO ACTIVATE THE BROADCOM DRIVER THAT POPS UP UNDER THE RESTRICTED DRIVERS*****



My problem:
I installed 8.10 today to see if my wireless would work out of the box. It seems to detect my wireless card this time, but for some reason it still won't work. I have a Broadcom BCM4311 [AirForce 54g] card. This is what comes up when I do sudo lshw -C network
```
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```
It seems as though it might be disabled for some reason:confused:How would I enable it? Also if any of you want to know, Yes, it is turned on at least my button shows that its on.

---

### Post by Ayuthia on 2008-10-30
> **brandon88tube said:**
> I installed 8.10 today to see if my wireless would work out of the box. It seems to detect my wireless card this time, but for some reason it still won't work. I have a Broadcom BCM4311 [AirForce 54g] card. This is what comes up when I do sudo lshw -C network
```
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```
It seems as though it might be disabled for some reason:confused:How would I enable it? Also if any of you want to know, Yes, it is turned on at least my button shows that its on.

Go into System->Administration->Hardware Drivers and see if the Broadcom STA driver (not the Broadcom b43 version) is available.  If it is, enable it and it should work.

---

### Post by brandon88tube on 2008-10-30
When I go to Administration>Hardware Drivers all that comes up is the ATI driver, which I haven't enabled.

---

### Post by Ayuthia on 2008-10-30
> **brandon88tube said:**
> When I go to Administration>Hardware Drivers all that comes up is the ATI driver, which I haven't enabled.

Can you go into the Terminal and post the results of:
```
ls /lib/modules/`uname -r`/volatile
```
The ` is a backquote and not a single quote '.  To check this, type this into the Terminal:
```
echo `uname -r`
```If you used the correct quote, it will return the kernel version.  If you did not use the correct one, it will return uname -r.

If I recall correctly, /lib/modules/`uname -r`/volatile is where they store the wl.ko file (the proprietary Broadcom driver).

---

### Post by brandon88tube on 2008-10-30
This is what I got
```
brandon@ubuntu:~$ ls /lib/modules/`uname -r`/volatile
ath_hal.ko            ath_rate_onoe.ko    wlan.ko           wlan_wep.ko
ath_pci.ko            ath_rate_sample.ko  wlan_scan_ap.ko   wlan_xauth.ko
ath_rate_amrr.ko      wlan_acl.ko         wlan_scan_sta.ko  wl.ko
ath_rate_minstrel.ko  wlan_ccmp.ko        wlan_tkip.ko
```
This is a little time consuming as I have to copy over stuff to my usb drive and bring back to my other computer. So if my replies are slow that is why.

---

### Post by Ayuthia on 2008-10-30
> **brandon88tube said:**
> This is what I got
```
brandon@ubuntu:~$ ls /lib/modules/`uname -r`/volatile
ath_hal.ko            ath_rate_onoe.ko    wlan.ko           wlan_wep.ko
ath_pci.ko            ath_rate_sample.ko  wlan_scan_ap.ko   wlan_xauth.ko
ath_rate_amrr.ko      wlan_acl.ko         wlan_scan_sta.ko  wl.ko
ath_rate_minstrel.ko  wlan_ccmp.ko        wlan_tkip.ko
```
This is a little time consuming as I have to copy over stuff to my usb drive and bring back to my other computer. So if my replies are slow that is why.

Sorry.  Can you try the following:
```
sudo modprobe -r b43 ssb bcm43xx wl
sudo depmod -a
sudo modprobe wl
sudo /etc/init.d/networking restart
```

Hopefully that will get it started.  If it does, then we will need to blacklist the b43 and ssb modules.  I will try to download the Intrepid CD and see if I can duplicate this issue (I have been upgrading since the alpha stages).

---

### Post by brandon88tube on 2008-10-30
Quick question before I do this. What exactly am I doing with those commands? It looks like I'm removing something and if I am how would I get it back just in case?

---

### Post by Ayuthia on 2008-10-30
> **brandon88tube said:**
> Quick question before I do this. What exactly am I doing with those commands? It looks like I'm removing something and if I am how would I get it back just in case?

Sorry about that.  This is only going to work for the current session.  As soon as you reboot, it will go away.  What this is going to do is remove the possible conflicting wireless drivers.  The depmod command is going to build the dependencies for the modules again.  It is most likely not needed but just doing in case.  The third command is going to load the wl module that should work for your card.  The final command is restarting your network.

---

### Post by atomizer on 2008-10-30
Same problem here
there is no module bcm43xx.

tom@tom-laptop:~$ sudo modprobe -r b43 ssb bcm43xx wl
[sudo] password for tom: 
FATAL: Module bcm43xx not found.
tom@tom-laptop:~$ sudo depmod -a
tom@tom-laptop:~$ sudo modprobe wl
tom@tom-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.

---

### Post by Ayuthia on 2008-10-30
> **atomizer said:**
> Same problem here
there is no module bcm43xx.

tom@tom-laptop:~$ sudo modprobe -r b43 ssb bcm43xx wl
[sudo] password for tom: 
FATAL: Module bcm43xx not found.
tom@tom-laptop:~$ sudo depmod -a
tom@tom-laptop:~$ sudo modprobe wl
tom@tom-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.

I forgot about bcm43xx.  It was removed in this kernel.  That is ok.  We did not want that module so if it is not there, it is ok.

As for the last part, I have not seen that before.  Can you post your lshw -C network information?  I would like to see what network cards you have.

---

### Post by brandon88tube on 2008-10-30
Yeah, I get the FATAL: Module bcm43xx not found. I also went through the steps and nothing happened probably because it got that fatal error.

---

### Post by atomizer on 2008-10-30
System did hang in the last minute. 
(and yes I did reboot after upgrade)
After reboot wireless worked :S
only 1 of my usb-ports don't recognises my mouse anymore

but anyway I put lshw -C network:

tom@tom-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:d9:8d:01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:18:39:4c:07:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:40:e8:5e:32:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Hector40 on 2008-10-30
Hi,
  I have a similar situation. I did a fresh install of 8.10 because wireless had stopped working on 8.04.  

  After installing 8.10 a window popped up and told me that there was an updated driver for my system.  I said yes to install it and it installed the B43legacy drivers.

  When I go to the Hardware Drivers it shows the Broadcom B43legacy wireless driver.  I have BCM4306 rev. 02 on a Dell Inspiron 5100.

  I ran the following with no error or messages but wireless is still not working.

sudo modprobe -r b43 wl
sudo depmod -a
sudo modprobe b43legacy
sudo /etc/init.d/networking restart

---

### Post by DollaBillz217 on 2008-10-30
I just installed 8.10 on my laptop and was having the exact same issue at first.  I have a built-in Broadcom BCM4318 AirForce One 54g Wireless controller.  When I issue the lshw -C network command it shows my wireless card.  At first it wouldn't connect, but what I had to do was hook up my laptop to my router via a wired connection so I could access the internet.  Then I clicked on System -> Administration -> Hardware Drivers.  Then under there there was a Broadcom B43 Wireless driver option.  I clicked on it and clicked activate and it worked.  Just remember that while you are doing this you CANNOT have open any other file manager or it will spew out a /var/cache/lock error.  Hope this helps :-)

---

### Post by Hector40 on 2008-10-30
> **DollaBillz217 said:**
> I just installed 8.10 on my laptop and was having the exact same issue at first.  I have a built-in Broadcom BCM4318 AirForce One 54g Wireless controller.  When I issue the lshw -C network command it shows my wireless card.  At first it wouldn't connect, but what I had to do was hook up my laptop to my router via a wired connection so I could access the internet.  Then I clicked on System -> Administration -> Hardware Drivers.  Then under there there was a Broadcom B43 Wireless driver option.  I clicked on it and clicked activate and it worked.  Just remember that while you are doing this you CANNOT have open any other file manager or it will spew out a /var/cache/lock error.  Hope this helps :-)

Thanks DollaBillz217, but I wish it were that simple.  I already checked the Hardware Drivers dialogue box and it shows my wireless driver activated.

---

### Post by brandon88tube on 2008-10-30
Mine doesn't even seem to show up in the driver list.

---

### Post by sandpaperback on 2008-10-30
My Broadcom 4318 is also not working and not showing up in the Hardware Drivers screen. :(

---

### Post by Hector40 on 2008-10-30
I went to the following post and followed the directions hoping to be able to install my drivers with ndiswrapper and got the results below.

[http://ubuntuforums.org/showthread.php?t=201902&highlight=wl_apsta](http://ubuntuforums.org/showthread.php?t=201902&highlight=wl_apsta)

> hpuig@hpuig-laptop:~$ sudo ndiswrapper -i ~/hpuig/bcm43xx/bcmwl5.inf
driver bcmwl5 is already installed


So it looks like my driver is not the problem. It seems like the wireless is not turned on and not detecting any networks. Maybe it is a conflict with another driver.

---

### Post by brandon88tube on 2008-10-30
Every time I create a network it pops up with a notification saying Network Disconnected.

---

### Post by Ayuthia on 2008-10-30
> **brandon88tube said:**
> Yeah, I get the FATAL: Module bcm43xx not found. I also went through the steps and nothing happened probably because it got that fatal error.

If you received nothing else, then the wl module might have loaded just fine.  Try the following:
```
sudo modprobe -r b43 ssb wl
sudo depmod -a
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

---

### Post by Ayuthia on 2008-10-30
> **Hector40 said:**
> Thanks DollaBillz217, but I wish it were that simple.  I already checked the Hardware Drivers dialogue box and it shows my wireless driver activated.

You might have to try the ndiswrapper route.  The bcm43xx driver has been removed from the kernel and for some reason the 4306 rev 02 has not been too happy in Ubuntu using the b43 driver.

You might try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
The guide should work for Intrepid because there are no real differences in the instructions between Hardy and Intrepid.

EDIT:  I just saw your other post where you have already installed ndiswrapper. You can try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If it does not work, can you let us know if this is a fresh install or an upgrade?  Also, did you compile ndiswrapper or are you using the repositories?  If it is compiled and you have not compiled after the upgrade, then you will need to do recompile because it is a different kernel version.

---

### Post by Ayuthia on 2008-10-30
> **atomizer said:**
> System did hang in the last minute. 
(and yes I did reboot after upgrade)
After reboot wireless worked :S
only 1 of my usb-ports don't recognises my mouse anymore

but anyway I put lshw -C network:

tom@tom-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:d9:8d:01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:18:39:4c:07:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:40:e8:5e:32:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

You have a 4318 card.  You will need to use the b43 driver and not the Broadcom STA (wl) driver.  You will have to enable it through System->Administration->Hardware Drivers or else go into Synaptic and install b43-fwcutter.  It looks like you have an internet connection so when it asks to find the firmware for you, say yes.

---

### Post by Ayuthia on 2008-10-30
> **sandpaperback said:**
> My Broadcom 4318 is also not working and not showing up in the Hardware Drivers screen. :(

If you have a internet connection, you can try to go into Synaptic and install b43-fwcutter.  It will ask if you want it to find the firmware for you.  Say yes and it will download the firmware and cut out the needed parts for the driver.

---

### Post by ercdvs on 2008-10-30
same problem here with a dell 1705

the restricted 'wl' drivers were enabled, but wireless was not working.

apt-get update / upgrade pulled a mess of new kernel updates.

Now I get the broadcom restricted drivers.  its frustrating to pull a freshly installed system and still need drivers for basic functionality ..

Would these be included on the dvd iso rather then the cd iso ?

---

### Post by Ayuthia on 2008-10-30
> **ercdvs said:**
> same problem here with a dell 1705

the restricted 'wl' drivers were enabled, but wireless was not working.

apt-get update / upgrade pulled a mess of new kernel updates.

Now I get the broadcom restricted drivers.  its frustrating to pull a freshly installed system and still need drivers for basic functionality ..

Would these be included on the dvd iso rather then the cd iso ?

Are you using 8.10?  I am thinking that there are no updates in 8.10 yet because it was just released today. EDIT: I am mistaken.  There are updates out there (including kernel updates).

The open source drivers (b43) do require some information from a firmware file.  Unfortunately the firmware has rules set in there where Ubuntu cannot include them on the CD/DVD.

However, if you are using the 4311, 4312, 4321, 4322, or 4328 card, you should be able to use the wl driver without any additional download.

You might try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```It sounds like there might be a conflict in the wireless drivers.  If you are still having problems and have an internet connection, can you post the results of:
```
lspci -nn
lshw -C network
```

EDIT: I decided to download the Intrepid liveCD (I have been using Intrepid during the alpha stages) and ran the liveCD to see what is happening.  I did find out that there are updates out there.  I have also found that there are some issues with the wl driver also.  It looks like it was missing a dependency.  If you are using a fresh install of Intrepid, don't have an internet connection, and have the Broadcom STA (wl) driver as an option but can't get it to work, please try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
```
Hopefully that will get you connected.

---

### Post by brandon88tube on 2008-10-30
> **Ayuthia said:**
> If you received nothing else, then the wl module might have loaded just fine.  Try the following:
```
sudo modprobe -r b43 ssb wl
sudo depmod -a
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

I did that and when I did the iwlist scan it came up with
lo   Interface doesn't support scanning.
eth0 Interface doesn't support scanning.

---

### Post by Scott-271 on 2008-10-30
I'm running the bcm4318 card, and I really hope this isn't going to be a problem like it was in 8.04. I just dl'd 8.10 and plan on installing it tomorrow, I'll be back if I'm having issues.

Scott

---

### Post by Ayuthia on 2008-10-30
> **brandon88tube said:**
> I did that and when I did the iwlist scan it came up with
lo   Interface doesn't support scanning.
eth0 Interface doesn't support scanning.

Can you now post the results of:
```
sudo ifconfig wlan0 up
sudo ifconfig eth1 up
lsmod|grep -e b4 -e ssb -e wl
modprobe --show-depends wl
```

---

### Post by sandpaperback on 2008-10-30
Foolish me.  I had installed the Intrepid RC the other day.  Once I updated everything today my card did show up in the Hardware Drivers dialog and after a reboot it seems all is well.

And that's for the 4318 by the way.

---

### Post by ercdvs on 2008-10-30
> **Ayuthia said:**
> Are you using 8.10?  I am thinking that there are no updates in 8.10 yet because it was just released today. 

The open source drivers (b43) do require some information from a firmware file.  Unfortunately the firmware has rules set in there where Ubuntu cannot include them on the CD/DVD.

However, if you are using the 4311, 4312, 4321, 4322, or 4328 card, you should be able to use the wl driver without any additional download.

You might try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```It sounds like there might be a conflict in the wireless drivers.  If you are still having problems and have an internet connection, can you post the results of:
```
lspci -nn
lshw -C network
```

Thats the point, it is a fresh 8.10.  Judging by the sheer number of broadcom threads popping up, I see that its a problem for a lot of people..

It doesn't seem like a problem to include the driver, but leave it disabled, like the ATI driver is.

---

### Post by Scott-271 on 2008-10-30
Thanks Sandpaperback, that gives me hope!!!

\\:D/

---

### Post by Ayuthia on 2008-10-30
For those with the 4306 or 4318 cards, can you post the lspci -nnm for your card?  It will help provide the chipset, revision, and subvendor information for your card.  From what I have seen in Hardy, it has been hit and miss for those two cards and it looks like Intrepid has gotten a little better, but there is not enough results out there yet.

---

### Post by Scott-271 on 2008-10-30
Thanks Ayuthia, as soon as I get 8.10 installed tomorrow - I'll post. 

Scott

---

### Post by gaelfx on 2008-10-30
Have you installed and ran b43-fwcutter in Synaptic? Worked for me.

---

### Post by Scott-271 on 2008-10-30
I'll be installing tomorrow morning, as much as I want to wait up and do this tonight - I'll wait: beer+food+getting sick=need sleep!

I'll contribute my successes/failures with 4318 as they come.

Scott

---

### Post by Hector40 on 2008-10-30
> **Ayuthia said:**
> ...
EDIT:  I just saw your other post where you have already installed ndiswrapper. You can try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If it does not work, can you let us know if this is a fresh install or an upgrade?  Also, did you compile ndiswrapper or are you using the repositories?  If it is compiled and you have not compiled after the upgrade, then you will need to do recompile because it is a different kernel version.

I tried the commands that you suggested and now when I click on the network manager icon the header for wireless options doesn't show up. You can see below the results from the terminal when I entered the commands. I can't remove ssb because it is being used by b44. And if I remove b44 then I loose my wired network connection (eth0). It has happened to me before.

> -laptop:~$ sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
FATAL: Module ssb is in use.
laptop:~$ sudo modprobe ndiswrapper
laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


I did a fresh install of the release candidate of 8.10 and then updated today to the full version through the update manager. After that ndiswrapper was installed when the system installed the b43legacy driver. I will probably do a fresh install of the final 8.10 tomorrow and start from scratch. To many things have been installed and uninstalled.

Here are the results from 
> laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [2560]" -r03 "" ""
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [2561]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [24c2]" -r02 "Intel Corporation [8086]" "Device [24c0]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [24c4]" -r02 "Intel Corporation [8086]" "Device [24c0]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [24c7]" -r02 "Intel Corporation [8086]" "Device [24c0]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [24cd]" -r02 -p20 "Intel Corporation [8086]" "Device [24c0]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 PCI Bridge [244e]" -r82 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [24c0]" -r02 "" ""
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801DB (ICH4) IDE Controller [24cb]" -r02 -p8a "Intel Corporation [8086]" "Device [24c0]"
00:1f.5 "Multimedia audio controller [0401]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [24c5]" -r02 "Dell [1028]" "Device [0149]"
00:1f.6 "Modem [0703]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [24c6]" -r02 "Conexant Systems, Inc. [14f1]" "Device [5422]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon Mobility M7 LW [Radeon Mobility 7500] [4c57]" "Dell [1028]" "Device [0149]"
02:01.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401 100Base-T [4401]" -r01 "Dell [1028]" "Device [0149]"
02:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "Device [0001]"
02:04.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI4510 PC card Cardbus Controller [ac44]" -r02 "Dell [1028]" "Device [0149]"
02:04.1 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "PCI4510 IEEE-1394 Controller [8029]" -p10 "Dell [1028]" "Device [0149]"

---

### Post by Ayuthia on 2008-10-30
> **Hector40 said:**
> I tried the commands that you suggested and now when I click on the network manager icon the header for wireless options doesn't show up. You can see below the results from the terminal when I entered the commands. I can't remove ssb because it is being used by b44. And if I remove b44 then I loose my wired network connection (eth0). It has happened to me before.
If that is the case, you should try the following:
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan[/code]
Since you need to have the b44 driver, you just need to load the b44 driver after ndiswrapper (ssb will automatically load because it is needed by b44).

---

### Post by Ayuthia on 2008-10-31
> **Ayuthia said:**
> Can you now post the results of:
```
sudo ifconfig wlan0 up
sudo ifconfig eth1 up
lsmod|grep -e b4 -e ssb -e wl
```

I just downloaded the liveCD and tried to install the Broadcom STA driver (running in the liveCD--I have Intrepid installed from the alpha stage on my laptop) and found a slight problem with how it is loaded. It looks like it is missing a dependency.  You might try the following to see if you can get it to work:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

From what I can tell, it looks like ieee80211_crypt_tkip is not being loaded.  The wl driver does need it (based on the info from [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)).

---

### Post by atomizer on 2008-10-31
Seems like I had to disable then re-enable the hardwaredriver for broadcom.
(_and reboot_)
I upgraded from 8.04
wireless works like a charm now.

lspci -nnm:
blah blah
03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Linksys [1737]" "Device [0049]"
blah blah

---

### Post by brandon88tube on 2008-10-31
I ran these commands
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

Didn't get any error messages, but the wireless did not work. In fact when I clicked the networking icon wireless was nowhere to be found. Even though sudo /etc/init.d/networking restart said [ OK ]
It never really restarted it for me.

---

### Post by Ayuthia on 2008-10-31
> **brandon88tube said:**
> I ran these commands
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

Didn't get any error messages, but the wireless did not work. In fact when I clicked the networking icon wireless was nowhere to be found. Even though sudo /etc/init.d/networking restart said [ OK ]
It never really restarted it for me.

Did the last command produce any wireless sites?

---

### Post by brandon88tube on 2008-10-31
Hmm, seems I missed that last command when I did it. Sorry about that. I will try that once I reboot into Ubuntu.

---

### Post by brandon88tube on 2008-10-31
I ran all of these commands again and made sure I did them all this time.
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

When I get to the iwlist scan it outputs

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

pan0 Interface doesn't support scanning.

---

### Post by bung-foo on 2008-10-31
> **Scott-271 said:**
> I'm running the bcm4318 card, and I really hope this isn't going to be a problem like it was in 8.04. I just dl'd 8.10 and plan on installing it tomorrow, I'll be back if I'm having issues.

Scott

Heads up here, I've got a broadcom 4318 as well. All I had to do to get it to work was run synaptic, update its sources, install b43-fwcutter. have it download the firmware and reboot.

Hope that saves you some time. :-)

---

### Post by underdog512 on 2008-10-31
> **Ayuthia said:**
> For those with the 4306 or 4318 cards, can you post the lspci -nnm for your card?  It will help provide the chipset, revision, and subvendor information for your card.  From what I have seen in Hardy, it has been hit and miss for those two cards and it looks like Intrepid has gotten a little better, but there is not enough results out there yet.

My 4306 card is not showing up under hardware drivers. plus the light is not even coming on.

```
02:06.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Hewlett-Packard Company [103c]" "Device [12f4]"

```

---

### Post by legolos13 on 2008-10-31
hey i have this same problem where it says network disabled.... i have a Dell Wireless 1390 Wlan MiniCard
installed driver, wi fi light is on but it still says disabled how do i enable?

---

### Post by brandoncolorado on 2008-10-31
> **bung-foo said:**
> Heads up here, I've got a broadcom 4318 as well. All I had to do to get it to work was run synaptic, update its sources, install b43-fwcutter. have it download the firmware and reboot.

Hope that saves you some time. :-)

I installed the restricted driver after using wired internet to update.  I restarted, and it says the driver is activated.  However, there are still no wireless networks listed.  It worked for me under 8.04.

Any ideas?   (using BCM4318)

---

### Post by brandon88tube on 2008-10-31
Well so far nothing seems to be working for my 4311 Airforce 54g. I am really starting to doubt that improved wireless info they stated for 8.10

---

### Post by chevylvr on 2008-10-31
I was able to install fw-cutter and let it install the firmware files and it started to work. The only issue is that it will only connect at 1mbs/sec. I have not found a good solution. I have a linksys card in another system and it does the same thing as far as the connection. It did the same thing in Hardy, I was hoping that they would fix that.

---

### Post by Scott-271 on 2008-10-31
> **bung-foo said:**
> Heads up here, I've got a broadcom 4318 as well. All I had to do to get it to work was run synaptic, update its sources, install b43-fwcutter. have it download the firmware and reboot.

Hope that saves you some time. :-)

Thanks bung-foo!!!! I just finished getting 8.10 installed and I'll have a chance to play around with it later. Quick question, did you have a wired connection also? I do not, that's why I ask. Did you do all that with just wireless?

Thanks again,
Scott

---

### Post by thefrozenpenguin on 2008-10-31
I have followed some of the advice on this thread and now have a working 4318 card, but don't know how to automate the process.

I have the b43 driver installed and activated via the "Hardware Drivers" in the System menu on a fresh install of 8.10, after re-boot I have to enter the following on the terminal to activate and connect to my wireless network:

sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe b44
sudo modprobe -r b43
sudo modprobe b43

When the first command is entered the Network manager appears in panel, when the last entry is run to re-start the b43 driver the card acquires an IP address from my wireless router.

How do I automate this?

Iain

---

### Post by MistressSheena on 2008-10-31
I'm using 8.04, (kubuntu)
I got my wireless card's firmware dealt with, and it can detect and connect to my router without encryption.

Now, when I enable WEP... it won't connect. And WPA isn't even an option. o_O;

I need guidance, please. ^_^

Just tell me what you would like to see, and I'll do what I can.

---

### Post by bung-foo on 2008-10-31
> **Scott-271 said:**
> Thanks bung-foo!!!! I just finished getting 8.10 installed and I'll have a chance to play around with it later. Quick question, did you have a wired connection also? I do not, that's why I ask. Did you do all that with just wireless?

Thanks again,
Scott

Yeah I had the laptop conected to my wired network while I updated synaptic sources and installed b43-fwcutter. After I rebooted the wireless network automatically started up.


Bung-Foo

---

### Post by eternal_sage on 2008-10-31
ok. i suppose i'll consolidate my earlier posts in other threads into this thread, since i've been having these problems since RC came out.

my wife has a BCM4328 and i can get it on the web w/ the following

```

courtney@Cortana:~$ sudo modprobe -r b43 ssb wl
FATAL: Module ssb is in use.
courtney@Cortana:~$ sudo modprobe ieee80211_crypt_tkip
courtney@Cortana:~$ sudo modprobe wl
courtney@Cortana:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
courtney@Cortana:~$

```

but it does not stick. i have installed and utilized b43-fwcutter, but it still will not stick on reboot. i have removed ndiswrapper completely, because it was a waste of time is is obviously not needed.

also, this is the lspci -nnm

```

courtney@Cortana:~$ lspci -nnm
 ---edit---
03:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401-B0 100Base-TX [170c]" -r02 "Dell [1028]" "Device [01d7]"
 ---edit---
0c:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4328 802.11a/b/g/n [4328]" -r01 "Dell [1028]" "Device [0009]"

```

and this is the lshw -C network

```

courtney@Cortana:~$ sudo lshw -C network
[sudo] password for courtney: 
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:cf:08:65:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.5 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:42:f3:4a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:12:a5:4c:6d:ce
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by brandon88tube on 2008-10-31
Well I was hoping others with similar issues would post in here to have a big source to help people trying to get Broadcom wireless working in 8.10. So far though most people including myself cannot get this to work yet.

---

### Post by eternal_sage on 2008-10-31
yea, and looking around this forum, it seems 8.10 totally screwed a large portion of people's wireless. funny, considering i thought the idea was UN-screwing a large portion of people :D.

oh well. if this keeps it up, i'm going back to 8.04.1. i love Ubuntu alot, but this release is disheartening, to say the least.

---

### Post by MistressSheena on 2008-10-31
Haha. I'm on 8.04.. I'm trying to get WEP to work for my connection.
I can connect just fine without encryption. I just need to figure out that small something in my router settings that's making it impossible for my lappy to connect.

---

### Post by brandon88tube on 2008-10-31
> **eternal_sage said:**
> yea, and looking around this forum, it seems 8.10 totally screwed a large portion of people's wireless. funny, considering i thought the idea was UN-screwing a large portion of people :D.

oh well. if this keeps it up, i'm going back to 8.04.1. i love Ubuntu alot, but this release is disheartening, to say the least.

Yeah, they tried to improve wireless with this release, but it seems that it did more harm. This is very disheartening and I might just go back to 8.04.1 because I also have an issue where my fan won't turn on in 8.10, which will eventually fry my laptop. Getting back to the wireless though, it would be helpful if other Broadcom users that have their wireless working, if they could post what worked for them.

---

### Post by kolibri on 2008-10-31
I couldn't get wireless working in 8.04, thought I'd try 8.10, still no wireless.

System=>hardware drivers shows wl not activated, but no other drivers.

going through the other posts here, my computer sees the broadcom 4312 card.

Sudo modprobe -r b43 ssb ndiswrapper wl
gives me an error: FATAL Module ssb is in use.

Sudo ifconfig wlan0 up
gives me an error:  wlan0:  ERROR while getting interface flags:  No such device.

I removed and then reinstalled the b43-fwcutter, and said yes if I wanted it to fetch and install.

---

### Post by MistressSheena on 2008-10-31
Well, as far as how I got mine working...
I just did the thing where when the driver window popped up, I enabled the B43 driver to find/extract the firmware, and then enabled the STA driver, and then rebooted...

And it worked. I could connect to my wireless.

.....Without encryption. I want to connect to it while it is encrypted. 

I'm still at a loss for that.

Edit: Yes, I installed the b43xx-fwcutter, actually. I remember that's the driver type I have when doing previous attemps with ndiswrapper.

---

### Post by billli on 2008-10-31
Hello all:
I just did a fresh install of ubuntu 8.10, and currently only wl is enabled and Broadcom B43 wireless driver is disabled, and my wireless is not working, any suggestions? 

Thanks;



iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

 lspci -nn:
```

00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [27a0]" -r03 "Dell [1028]" "Device [01bd]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [27a1]" -r03 "" ""
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801G (ICH7 Family) High Definition Audio Controller [27d8]" -r01 "Dell [1028]" "Device [01bd]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 1 [27d0]" -r01 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 4 [27d6]" -r01 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #1 [27c8]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #2 [27c9]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #3 [27ca]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #4 [27cb]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB2 EHCI Controller [27cc]" -r01 -p20 "Dell [1028]" "Device [01bd]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re1 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r01 "Dell [1028]" "Device [01bd]"
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "82801GBM/GHM (ICH7 Family) SATA IDE Controller [27c4]" -r01 -p80 "Dell [1028]" "Device [01bd]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801G (ICH7 Family) SMBus Controller [27da]" -r01 "Dell [1028]" "Device [01bd]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon Mobility X1400 [7145]" "Dell [1028]" "Device [2003]"
03:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401-B0 100Base-TX [170c]" -r02 "Dell [1028]" "Device [01af]"
03:01.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -p10 "Dell [1028]" "Device [01bd]"
03:01.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r19 -p01 "Dell [1028]" "Device [01bd]"
03:01.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r0a "Dell [1028]" "Device [01bd]"
03:01.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -r05 "Dell [1028]" "Device [01bd]"
0b:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4328 802.11a/b/g/n [4328]" -r01 "Dell [1028]" "Device [0009]"

```

sudo lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:bf:01:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=129.97.231.22 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:42:1b:12:8e:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Ayuthia on 2008-10-31
> **legolos13 said:**
> hey i have this same problem where it says network disabled.... i have a Dell Wireless 1390 Wlan MiniCard
installed driver, wi fi light is on but it still says disabled how do i enable?

If you have an internet connection in Ubuntu without wireless, either the b43 or Broadcom STA (wl) driver will work.  You should be able to select the Broadcom STA driver from System->Administration->Hardware Drivers.  If you have not run any updates you might need to go into the Terminal and do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If it does not connect, please post the following results from the Terminal:
```
lsmod|grep -e b4 -e ssb -e wl -e ieee80211
modprobe --show-depends wl
lshw -C network
```

---

### Post by Ayuthia on 2008-10-31
> **chevylvr said:**
> I was able to install fw-cutter and let it install the firmware files and it started to work. The only issue is that it will only connect at 1mbs/sec. I have not found a good solution. I have a linksys card in another system and it does the same thing as far as the connection. It did the same thing in Hardy, I was hoping that they would fix that.

Can you post your lspci -nnm info?  It will help us see which card is producing those results.

---

### Post by Ayuthia on 2008-10-31
> **thefrozenpenguin said:**
> I have followed some of the advice on this thread and now have a working 4318 card, but don't know how to automate the process.

I have the b43 driver installed and activated via the "Hardware Drivers" in the System menu on a fresh install of 8.10, after re-boot I have to enter the following on the terminal to activate and connect to my wireless network:

sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe b44
sudo modprobe -r b43
sudo modprobe b43

When the first command is entered the Network manager appears in panel, when the last entry is run to re-start the b43 driver the card acquires an IP address from my wireless router.

How do I automate this?

Iain

Just add those commands to /etc/rc.local without the sudo and those commands will run when the system starts up.

---

### Post by Ayuthia on 2008-10-31
> **eternal_sage said:**
> ok. i suppose i'll consolidate my earlier posts in other threads into this thread, since i've been having these problems since RC came out.

my wife has a BCM4328 and i can get it on the web w/ the following

```

courtney@Cortana:~$ sudo modprobe -r b43 ssb wl
FATAL: Module ssb is in use.
courtney@Cortana:~$ sudo modprobe ieee80211_crypt_tkip
courtney@Cortana:~$ sudo modprobe wl
courtney@Cortana:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
courtney@Cortana:~$

```


You have a b44 driver for your ethernet card.  Because of this, you will need to have a couple extra commands:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```

---

### Post by Ayuthia on 2008-10-31
> **kolibri said:**
> I couldn't get wireless working in 8.04, thought I'd try 8.10, still no wireless.

System=>hardware drivers shows wl not activated, but no other drivers.

going through the other posts here, my computer sees the broadcom 4312 card.

Sudo modprobe -r b43 ssb ndiswrapper wl
gives me an error: FATAL Module ssb is in use.

Sudo ifconfig wlan0 up
gives me an error:  wlan0:  ERROR while getting interface flags:  No such device.

I removed and then reinstalled the b43-fwcutter, and said yes if I wanted it to fetch and install.

You will need to check and see if you have a Broadcom wired network card.  If you go into the Terminal and type:
```
lshw -C network
```If you see a Broadcom 44xx series card, then you have the b44 driver.  That means you will have to remove that driver before you can remove the ssb:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe b43 
sudo modprobe b44
sudo /etc/init.d/networking restart
```

---

### Post by eternal_sage on 2008-10-31
ok, i did these, and they also got her on the web. however, they still do not stick. how would i go about making them stick? thanks alot for everything so far!

---

### Post by Ayuthia on 2008-10-31
> **MistressSheena said:**
> Well, as far as how I got mine working...
I just did the thing where when the driver window popped up, I enabled the B43 driver to find/extract the firmware, and then enabled the STA driver, and then rebooted...

And it worked. I could connect to my wireless.

.....Without encryption. I want to connect to it while it is encrypted. 

I'm still at a loss for that.

Edit: Yes, I installed the b43xx-fwcutter, actually. I remember that's the driver type I have when doing previous attemps with ndiswrapper.

Can you post the results of:
```
lspci -nn
lshw -C network
```

---

### Post by Ayuthia on 2008-10-31
> **eternal_sage said:**
> ok, i did these, and they also got her on the web. will these stick, or is it still temporary? thanks!

This was temporary.  You can try this (it has not been thoroughly tested yet):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe ieee80211_crypt_tkip; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
The main part that I have added is the modprobe ieee80211_crypt_tkip.  This is the part that is missing in the dependencies for wl.

---

### Post by Ayuthia on 2008-10-31
> **billli said:**
> Hello all:
I just did a fresh install of ubuntu 8.10, and currently only wl is enabled and Broadcom B43 wireless driver is disabled, and my wireless is not working, any suggestions? 

Thanks;



iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

 lspci -nn:
```

00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [27a0]" -r03 "Dell [1028]" "Device [01bd]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [27a1]" -r03 "" ""
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801G (ICH7 Family) High Definition Audio Controller [27d8]" -r01 "Dell [1028]" "Device [01bd]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 1 [27d0]" -r01 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 4 [27d6]" -r01 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #1 [27c8]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #2 [27c9]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #3 [27ca]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #4 [27cb]" -r01 "Dell [1028]" "Device [01bd]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB2 EHCI Controller [27cc]" -r01 -p20 "Dell [1028]" "Device [01bd]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re1 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r01 "Dell [1028]" "Device [01bd]"
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "82801GBM/GHM (ICH7 Family) SATA IDE Controller [27c4]" -r01 -p80 "Dell [1028]" "Device [01bd]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801G (ICH7 Family) SMBus Controller [27da]" -r01 "Dell [1028]" "Device [01bd]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon Mobility X1400 [7145]" "Dell [1028]" "Device [2003]"
03:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401-B0 100Base-TX [170c]" -r02 "Dell [1028]" "Device [01af]"
03:01.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -p10 "Dell [1028]" "Device [01bd]"
03:01.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r19 -p01 "Dell [1028]" "Device [01bd]"
03:01.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r0a "Dell [1028]" "Device [01bd]"
03:01.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -r05 "Dell [1028]" "Device [01bd]"
0b:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4328 802.11a/b/g/n [4328]" -r01 "Dell [1028]" "Device [0009]"

```

sudo lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:bf:01:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=129.97.231.22 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:42:1b:12:8e:76
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Please try the following:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```

---

### Post by Ayuthia on 2008-10-31
> **brandon88tube said:**
> Yeah, they tried to improve wireless with this release, but it seems that it did more harm. This is very disheartening and I might just go back to 8.04.1 because I also have an issue where my fan won't turn on in 8.10, which will eventually fry my laptop. Getting back to the wireless though, it would be helpful if other Broadcom users that have their wireless working, if they could post what worked for them.

It is looking like your card is not wanting to connect with the wl driver.  Can you try the following again:
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
lsmod|grep -e wl -e b43
dmesg|grep 'wl '
```
The lsmod portion is checking to see what modules are being loaded for the wireless card.  The dmesg command is looking to see if any error messages are coming up for the wl driver.

You also have the other option of using the b43 driver.  It will require you to have to download the firmware.  I am going to post (in the next post) the instructions on what to download if you don't have a working connection in Ubuntu.

---

### Post by Ayuthia on 2008-10-31
For those of you who don't have a working connection in Ubuntu and cannot use the wl driver, here are some instructions on what to download so that you can install it in Ubuntu:

This will only work in Intrepid (and not the older versions of Ubuntu).  This is a revised version of this [thread]("http://ubuntuforums.org/showthread.php?t=779754")(changed because the firmware is different in Intrepid):

[B]Option 2
For those without a working internet connection[/B]

**If you have a Intrepid install CD, **
Insert your CD and do the following:
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter
```
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**
Now skip down to the Downloading Firmware section.

**If you don't have a Intrepid install CD**
You will have to find a place with a working internet connection.  Go to this link:
[http://packages.ubuntu.com/intrepid/utils/b43-fwcutter](http://packages.ubuntu.com/intrepid/utils/b43-fwcutter)
Download the version that you need--amd64 for 64-bit and i386 for 32-bit.  Copy the file to your home directory and do the following:
64-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_amd64.deb
```
It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

32-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
```
It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

**Downloading Firmware**
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```
Copy those files to your home directory.  In the Terminal/Konsole/xterm window do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

---

### Post by billli on 2008-10-31
> **Ayuthia said:**
> Please try the following:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```

it worked! thank you so much! :)

just wondering, what did those commands do? and why "sudo modprobe b44" instead of "sudo modprobe b43"?

and i should just use the wl driver instead of the broadcom b43 driver?

once again, thx

---

### Post by malachi1990 on 2008-10-31
Am I missing something here?  

All I had to do to enable wireless is turn on the wireless card, at least since the 2.6.24-21 kernel release.  Then it works out of the box better than the windows driver ever did (I did go through the hoops to get wireless in hardy).

And I have the Broadcomm 4318 wireless card, before anyone asks.

---

### Post by Ayuthia on 2008-10-31
> **malachi1990 said:**
> Am I missing something here?  

All I had to do to enable wireless is turn on the wireless card, at least since the 2.6.24-21 kernel release.  Then it works out of the box better than the windows driver ever did (I did go through the hoops to get wireless in hardy).

And I have the Broadcomm 4318 wireless card, before anyone asks.

The Broadcom STA (wl) driver does not support the 4318 card you will not be able to get your card to work without downloading something.  Your card might work with the b43 driver (it appears that Intrepid is working better with them than Hardy), but the system needs to download the firmware.  The other route is also ndiswrapper.

---

### Post by malachi1990 on 2008-10-31
> **Ayuthia said:**
> The Broadcom STA (wl) driver does not support the 4318 card you will not be able to get your card to work without downloading something.  Your card might work with the b43 driver (it appears that Intrepid is working better with them than Hardy), but the system needs to download the firmware.  The other route is also ndiswrapper.

Thanks for that info.  It's just that since the 2.6.24-21 kernel release, the linux driver has flawlessly supported my wireless (out of the box, w/out downloading anything that I can tell), which has left me surprised.  And a bit confused as to why these problems exist for others.

---

### Post by el2king on 2008-11-01
> **billli said:**
> it worked! thank you so much! :)

just wondering, what did those commands do? and why "sudo modprobe b44" instead of "sudo modprobe b43"?

and i should just use the wl driver instead of the broadcom b43 driver?

once again, thx

OK, so I tried the exact same thing with the modprobe commands, and I noticed that this worked for me too!  Is there like a script I can write to get this working correctly right on computer bootup?  I would definitely want this to be done automatically without manually executing the commands/script.  Thanks!  This has been a huge help!

Update: Actually I found that script and I tested it!  It does work.  Earlier in the email thread, a person created a file /etc/modprobe.d/wl, and it does work!  I'm glad to finally be rid of these annoying wireless problems.  Yes!!!

---

### Post by kolibri on 2008-11-01
> **Ayuthia said:**
> You will need to check and see if you have a Broadcom wired network card.  If you go into the Terminal and type:
```
lshw -C network
```If you see a Broadcom 44xx series card, then you have the b44 driver.  That means you will have to remove that driver before you can remove the ssb:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe b43 
sudo modprobe b44
sudo /etc/init.d/networking restart
```

I have a 4312 Broadcom card

My result for the above:

kolibri@Fruhling:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3d:21:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.45 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:7b:e4:ab
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:e4:83:5f:c5:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kolibri@Fruhling:~$ sudo modprobe -r b43 b44 ssb ndiswrapper wl
kolibri@Fruhling:~$ sudo modprobe b43
kolibri@Fruhling:~$ sudo modprobeb44
sudo: modprobeb44: command not found
kolibri@Fruhling:~$ sudo modprobe b44
kolibri@Fruhling:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
kolibri@Fruhling:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

(how do I put that stuff in a scrolling box so i don't take up the whole page?)

It didn't seem to do anything, I think I'm going to try a clean install of intrepid rather than an upgrade.

---

### Post by thefrozenpenguin on 2008-11-01
Thanks Ayuthia will give that a try.

Iain :)

---

### Post by JohnBUK on 2008-11-01
How come I can download and run Puppy Linux from a USB stick and my Broadcom Wifi works first time (the first time this has ever happened) and yet when I try every live CD for Ubuntu I have never had any joy whatsoever? I have a Dell Inspiron 8600 and I'd love to be able to use Linux but find the whole thing so frustrating I go back to Windows XP every time.

---

### Post by eternal_sage on 2008-11-01
i'm sorry, but that didn't work either. i pasted that script into the console, hit enter, it ran, and on reboot, no dice. this is so frustrating! thank you for everything so far though!

---

### Post by Ayuthia on 2008-11-01
> **eternal_sage said:**
> i'm sorry, but that didn't work either. i pasted that script into the console, hit enter, it ran, and on reboot, no dice. this is so frustrating! thank you for everything so far though!

I think that you will need to blacklist b43:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -u
```
This will blacklist the b43 module and also update the initram so that the kernel will not load it into memory while booting.  Hopefully that will catch it so that the wl module will load more properly.

---

### Post by Ayuthia on 2008-11-01
> **JohnBUK said:**
> How come I can download and run Puppy Linux from a USB stick and my Broadcom Wifi works first time (the first time this has ever happened) and yet when I try every live CD for Ubuntu I have never had any joy whatsoever? I have a Dell Inspiron 8600 and I'd love to be able to use Linux but find the whole thing so frustrating I go back to Windows XP every time.

I have not tried out Puppy Linux yet, but my guess is that they are using the wl driver from Broadcom.  This will help it work right out of the box.  Intrepid was supposed to do the same thing, but it looks like the wl driver was not built correctly on the liveCD.

---

### Post by Ayuthia on 2008-11-01
> **kolibri said:**
> I have a 4312 Broadcom card

My result for the above:

kolibri@Fruhling:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3d:21:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.45 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:7b:e4:ab
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:e4:83:5f:c5:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kolibri@Fruhling:~$ sudo modprobe -r b43 b44 ssb ndiswrapper wl
kolibri@Fruhling:~$ sudo modprobe b43
kolibri@Fruhling:~$ sudo modprobeb44
sudo: modprobeb44: command not found
kolibri@Fruhling:~$ sudo modprobe b44
kolibri@Fruhling:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
kolibri@Fruhling:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

(how do I put that stuff in a scrolling box so i don't take up the whole page?)

It didn't seem to do anything, I think I'm going to try a clean install of intrepid rather than an upgrade.

The easy way to put things in a scrolling box is to paste the results into the post and then highlight it.  On the top of the edit window, there are some option buttons.  If you click on the # button, it will put them into a code box which does use scrolling.

Your lshw information looks like you should be using the wl driver.  Please try the following (It should not matter if you are upgrading or if it is a fresh install):
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
```

---

### Post by al_erola on 2008-11-01
SOLVED FOR ME!!!!!
Dell Inspiron E1505 Ubuntu Ibex

I was able to get the new wl driver working by using Ayuthia's steps (#6) and adding two more as marked.  Run these in a terminal.

sudo modprobe -r b43 ssb bcm43xx wl #bcm43xx is not needed
**sudo modprobe -r b44 #addition to remove eth0 driver**
sudo depmod -a
sudo modprobe wl
**sudo modprobe ssb #this is my addition**
sudo /etc/init.d/networking restart

al@E1505:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:66:c7:8c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

Please note that I haven't been able to automate this yet.  I need to run the steps in a terminal after I reboot.

---

### Post by eternal_sage on 2008-11-01
> **Ayuthia said:**
> I think that you will need to blacklist b43:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -u
```
This will blacklist the b43 module and also update the initram so that the kernel will not load it into memory while booting.  Hopefully that will catch it so that the wl module will load more properly.

you have been SO helpful! unfortunately that ALSO does not work! on reboot it is still not functioning. the series of commands still get it online however.

would it be viable to just make a script that ran those commands on startup to at least automate the process? if so, how would i do it? thank you so much for your time, as you have been an exemplar community member, and thats a fact!

---

### Post by Ayuthia on 2008-11-01
> **eternal_sage said:**
> you have been SO helpful! unfortunately that ALSO does not work! on reboot it is still not functioning. the series of commands still get it online however.

would it be viable to just make a script that ran those commands on startup to at least automate the process? if so, how would i do it? thank you so much for your time, as you have been an exemplar community member, and thats a fact!

The easy way to do this would be to put those commands into /etc/rc.local without the sudo in front.  rc.local is called when the system starts up so it will run those commands for you.  The process should work, but I generally don't recommend this because if you end up changing wireless drivers in the future, it will be hard to remember that you did this.  The /etc/modprobe.d/wl method is nicer because it only works when the wl driver is loaded.  I am recommending this for you because I can't seem to get the script working correctly for you at this time.

I will look into this further to see if there is a way to get it working differently.

---

### Post by Ayuthia on 2008-11-01
> **al_erola said:**
> SOLVED FOR ME!!!!!
Dell Inspiron E1505 Ubuntu Ibex

I was able to get the new wl driver working by using Ayuthia's steps (#6) and adding two more as marked.  Run these in a terminal.

sudo modprobe -r b43 ssb bcm43xx wl #bcm43xx is not needed
**sudo modprobe -r b44 #addition to remove eth0 driver**
sudo depmod -a
sudo modprobe wl
**sudo modprobe ssb #this is my addition**
sudo /etc/init.d/networking restart

al@E1505:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:66:c7:8c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

Please note that I haven't been able to automate this yet.  I need to run the steps in a terminal after I reboot.

Here are two ways that you can accomplish this.  The first is to add the commands into /etc/rc.local without the sudo command.  The second is to try the script in post 69:
[http://ubuntuforums.org/showpost.php?p=6077712&postcount=69](http://ubuntuforums.org/showpost.php?p=6077712&postcount=69)

Hope that helps.

---

### Post by eternal_sage on 2008-11-01
> **Ayuthia said:**
> The easy way to do this would be to put those commands into /etc/rc.local without the sudo in front.  rc.local is called when the system starts up so it will run those commands for you.  The process should work, but I generally don't recommend this because if you end up changing wireless drivers in the future, it will be hard to remember that you did this.  The /etc/modprobe.d/wl method is nicer because it only works when the wl driver is loaded.  I am recommending this for you because I can't seem to get the script working correctly for you at this time.

I will look into this further to see if there is a way to get it working differently.

this has fixed it. thank you! i doubt it will be a problem to have them in the rc.local, just because its unlikely she will want to switch drivers anytime soon. however, if you do find another good method, please let me know so i do it more properly. she just wants the net without fuss at the moment, and i'm inclined to let it slide, but since i'm the one who has to work on these things when they go bad, i prefer a better way as well!

just for my own knowledge, what exactly is modprobe? it seems to be toggling the arguments to it on and off, but i'm not sure. thanks!

---

### Post by mban23 on 2008-11-01
> **Ayuthia said:**
> If that is the case, you should try the following:
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan[/code]
Since you need to have the b44 driver, you just need to load the b44 driver after ndiswrapper (ssb will automatically load because it is needed by b44).

Ayuthia, thanks for this. I tried with wl instead of ndiswrapper and it worked. :)

Edit: Forgot to say, my wireless card is BCM4311

```

sudo modprobe -r b43 b43legacy b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan

```

---

### Post by Ayuthia on 2008-11-01
> **eternal_sage said:**
> this has fixed it. thank you! i doubt it will be a problem to have them in the rc.local, just because its unlikely she will want to switch drivers anytime soon. however, if you do find another good method, please let me know so i do it more properly. she just wants the net without fuss at the moment, and i'm inclined to let it slide, but since i'm the one who has to work on these things when they go bad, i prefer a better way as well!

just for my own knowledge, what exactly is modprobe? it seems to be toggling the arguments to it on and off, but i'm not sure. thanks!

modprobe is the command that is used to load and unload kernel modules.  Kernel modules are basically what Windows would call hardware drivers.  So as long as the *.ko (kernel module) file is found in /lib/modules and it's dependencies have been built (depmod -a), the modprobe command will work.  The depmod looks up all the dependencies for that kernel module and then will load all of them automatically for you.

---

### Post by NotonyourNelly on 2008-11-01
> **MistressSheena said:**
> Haha. I'm on 8.04.. I'm trying to get WEP to work for my connection.
I can connect just fine without encryption. I just need to figure out that small something in my router settings that's making it impossible for my lappy to connect.

Have you tied WEP 64/128-bit hex - this was the only way I can connect in 8.04....fingers crossed

---

### Post by brandon88tube on 2008-11-01
> **Ayuthia said:**
> It is looking like your card is not wanting to connect with the wl driver.  Can you try the following again:
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
lsmod|grep -e wl -e b43
dmesg|grep 'wl '
```
The lsmod portion is checking to see what modules are being loaded for the wireless card.  The dmesg command is looking to see if any error messages are coming up for the wl driver.

You also have the other option of using the b43 driver.  It will require you to have to download the firmware.  I am going to post (in the next post) the instructions on what to download if you don't have a working connection in Ubuntu.

For some reason after trying that code above, I restarted Ubuntu and now the Broadcom B43 driver comes up under the restricted drivers. I can't activate them yet as I do not have a way to connect my laptop online... I'll try to find a way to connect through an ethernet cable and see how it goes from there.

---

### Post by Ayuthia on 2008-11-01
> **brandon88tube said:**
> For some reason after trying that code above, I restarted Ubuntu and now the Broadcom B43 driver comes up under the restricted drivers. I can't activate them yet as I do not have a way to connect my laptop online... I'll try to find a way to connect through an ethernet cable and see how it goes from there.

You can try the steps in post #72:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

If you have another connection, you can grab the files and copy them over to your laptop.  You might also have to blacklist the wl driver so that it does not interfere with the b43 driver:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by Tokke on 2008-11-01
I have a simular problem like the topic starter however I tried the live cd before I installed 8.10 and after enabling the propietary driver my wireless connection worked like a charm.  But now that I installed 8.10 on the harddisk I cant get it to work anymore.  I even retried the live cd but it only worked one time (strange but true!)

sudo lshw -C network gives me:

  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:03:34:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.107 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:ec:c4:5c:bb:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:a0:7d:1e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

It is strange that I got it to work one time no?

---

### Post by Ayuthia on 2008-11-01
> **Tokke said:**
> I have a simular problem like the topic starter however I tried the live cd before I installed 8.10 and after enabling the propietary driver my wireless connection worked like a charm.  But now that I installed 8.10 on the harddisk I cant get it to work anymore.  I even retried the live cd but it only worked one time (strange but true!)

sudo lshw -C network gives me:

  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:03:34:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.107 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:ec:c4:5c:bb:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:a0:7d:1e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

It is strange that I got it to work one time no?
It is looking like the 4311 rev 02 card might not work as well.  Have you tried:
```
sudo modprobe -r b43 ssb wl
sudo depmod -a
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
```

If it does not work, can you post the results of:
```
lsmod|grep wl
uname -a
lspci -knnmd 14e4:*
```Thanks!

---

### Post by arnarg on 2008-11-01
I just upgraded from 8.04 (to 8.10) using the update manager, but now I can't connect to the wireless internet. At first it had some problems in 8.04, it got better when I installed ndiswrapper but it was good when the Broadcom STA driver was released. Now I'm using the STA driver and it "Sometimes" detects my wifi but never connects. I've tried to connect to wired internet to check for updates and successfully connected but there were no updates. Also, I have deactivated the STA driver and activated again.

**lspci**
> 02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)


**lshw -C network**
> *-network

description: Wireless interface

product: BCM4311 802.11b/g WLAN

vendor: Broadcom Corporation

physical id: 0

bus info: pci@0000:02:00.0

logical name: eth1

version: 01

serial: 00:1b:fc:27:87:3c

width: 32 bits

clock: 33MHz

capabilities: bus_master cap_list ethernet physical wireless

configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

*-network

description: Ethernet interface

product: L2 100 Mbit Ethernet Adapter

vendor: Attansic Technology Corp.

physical id: 0

bus info: pci@0000:06:00.0

logical name: eth0

version: a0

serial: 00:1b:fc:67:1f:b5

width: 64 bits

clock: 33MHz

capabilities: bus_master cap_list ethernet physical

configuration: broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 module=atl2 multicast=yes


**iwconfig**
> lo no wireless extensions.



eth0 no wireless extensions.



eth1 IEEE 802.11 Nickname:""

Access Point: Not-Associated 

---

### Post by Luk_Deisler on 2008-11-01
Hi I´ve got the same problem 
running Kubuntu 8.10
I´ve tried all the modprobe commands, but nothing worked for me so far :(


sudo lshw -C network 
```

 *-network:0                       
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation                                       
       physical id: 9                                                     
       bus info: pci@0000:00:09.0                                         
       version: 02                                                        
       width: 32 bits                                                     
       clock: 33MHz                                                       
       capabilities: bus_master                                           
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:bb:c3:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:9f:5f:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:4a:be:5b:0d:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lsmod|grep wl
nothing

uname -a
```
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
```

lspci -knnmd 14e4:*
```
00:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [120f]"

```


Any ideas :confused:

---

### Post by Angelbeast on 2008-11-01
I'm having a devil of a time with this too. I had such high hopes when i had read about 8.10's supposed wireless improvements *LOL*. HEre is my output from lspci -nnm

ron@ron-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS480 Host Bridge [5950]" -r01 "Hewlett-Packard Company [103c]" "Device [309b]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a3f]" "" ""
00:04.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a36]" "" ""
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]" -p10 "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]" -p10 "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]" -p20 "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "IXP SB400 SMBus Controller [4372]" -r11 "Hewlett-Packard Company [103c]" "Device [309b]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 IDE Controller [4376]" -p8a "Hewlett-Packard Company [103c]" "Device [309b]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-ISA Bridge [4377]" "" ""
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-PCI Bridge [4371]" -p01 "" ""
00:14.5 "Multimedia audio controller [0401]" "ATI Technologies Inc [1002]" "IXP SB400 AC'97 Audio Controller [4370]" -r02 "Hewlett-Packard Company [103c]" "Device [309b]"
00:14.6 "Modem [0703]" "ATI Technologies Inc [1002]" "SB400 AC'97 Modem Controller [4378]" -r02 "Hewlett-Packard Company [103c]" "Device [309b]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon XPRESS 200M 5955 (PCIE) [5955]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Hewlett-Packard Company [103c]" "Device [1355]"
06:04.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx21/x515 Cardbus Controller [8031]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:04.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "OHCI Compliant IEEE 1394 Host Controller [8032]" -p10 "Hewlett-Packard Company [103c]" "Device [309b]"
06:04.3 "Mass storage controller [0180]" "Texas Instruments [104c]" "PCIxx21 Integrated FlashMedia Controller [8033]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:04.4 "SD Host controller [0805]" "Texas Instruments [104c]" "PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [8034]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:06.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Hewlett-Packard Company [103c]" "Device [309b]"


I have tried ndiswrapper and now am using the firmwre included in the hardware driver menu both with no luck.

---

### Post by Tokke on 2008-11-01
@Ayuthia

It tried the code you proposed but that didn't do the trick.

lsmod|grep wl
nothing

uname -a
```
Linux laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
```

lspci -knnmd 14e4:*
```
06:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [4319]" -r02 "Hewlett-Packard Company [103c]" "Device [1359]"
```

Thanks for looking into it.

PS: I did a reinstallation of Ubuntu 8.10 and upgraded immediately without activating the proprietary drivers.  After the upgrade I dont see the wireless card in the proprietary drivers list anymore.

---

### Post by brandon88tube on 2008-11-01
Hey Tokke if you get anything to work let me know because I think I have the same wireless card as you. I am going to try some more stuff and if I find a solution I will most certainly post it for others.

---

### Post by brandon88tube on 2008-11-01
Ok, I did a fresh install of Ubuntu 8.10 and I was able to get my laptop hooked up to by ethernet. I first did some updates that came up, which included some kernel stuff. Then the Broadcom 43 drivers popped up again in the restricted drivers. I selected to activate them, but it just sat at 0%. I then popped up System Monitor and realized that it was running some network stuff so I let it be. It took a while, but the 0% finally went away and it seemed to install. I restarted Ubuntu and when it came up it started showing wireless networks around me! :D The only problem now is that I have WEP(Yeah I know we are getting a new router soon with at least WPA2) and it won't connect.

***Stating this again for others. If you can get an internet connection without wireless just for a short period of time by taking the computer and moving it close to your router and plugging it in via the ethernet cable or something do so. Then check for updates for the system as there should be some updates for the kernel etc. Then if you have the Broadcom driver pop up in the restricted drivers. Try to activate it even if it stays at 0% DO NOT PANIC AND CLOSE IT. JUST LEAVE IT BE FOR A WHILE. It took me around 30mins or so for it to finish. Be patient and if it is past 30mins and is still showing 0%, pop open System Monitor and check your network activity to see if anything is still running.

---

### Post by oosh50 on 2008-11-01
none of the above worked for me  (asus x50r ubuntu 8.10 BCM4311) wireless light goes off when login screen loads, broadcom STA drivers dont work!

---

### Post by Ayuthia on 2008-11-01
> **arnarg said:**
> I just upgraded from 8.04 (to 8.10) using the update manager, but now I can't connect to the wireless internet. At first it had some problems in 8.04, it got better when I installed ndiswrapper but it was good when the Broadcom STA driver was released. Now I'm using the STA driver and it "Sometimes" detects my wifi but never connects. I've tried to connect to wired internet to check for updates and successfully connected but there were no updates. Also, I have deactivated the STA driver and activated again.

**lspci**



**lshw -C network**



**iwconfig**

You might try the following since you had ndiswrapper in the previous version:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart

```I am thinking that there is a chance that the ndiswrapper driver is causing a conflict.  I have the same card as you and it took a little work but I was able to get it running when I was using the live CD.  I was using the wl driver with my installed version of Intrepid and it updated without issue.  Hopefully yours will work as well.

---

### Post by Ayuthia on 2008-11-01
> **Luk_Deisler said:**
> Hi I´ve got the same problem 
running Kubuntu 8.10
I´ve tried all the modprobe commands, but nothing worked for me so far :(


sudo lshw -C network 
```

 *-network:0                       
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation                                       
       physical id: 9                                                     
       bus info: pci@0000:00:09.0                                         
       version: 02                                                        
       width: 32 bits                                                     
       clock: 33MHz                                                       
       capabilities: bus_master                                           
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:bb:c3:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:9f:5f:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:4a:be:5b:0d:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lsmod|grep wl
nothing

uname -a
```
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
```

lspci -knnmd 14e4:*
```
00:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [120f]"

```


Any ideas :confused:

You will need to use the b43 module instead of the wl module.  The Broadcom STA (wl) module does not work with the 4318 cards.  You will need a wired connection in Ubuntu if you want to activate that module or else install b43-fwcutter.  If you don't have a connection in Ubuntu, you can try the information in post #72:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
It contains instructions on how to download the necessary files from another computer (or through Windows if you are dual-booting) to get the b43 modules working in Ubuntu.

---

### Post by Ayuthia on 2008-11-01
> **Angelbeast said:**
> I'm having a devil of a time with this too. I had such high hopes when i had read about 8.10's supposed wireless improvements *LOL*. HEre is my output from lspci -nnm

ron@ron-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS480 Host Bridge [5950]" -r01 "Hewlett-Packard Company [103c]" "Device [309b]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a3f]" "" ""
00:04.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a36]" "" ""
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]" -p10 "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]" -p10 "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]" -p20 "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "IXP SB400 SMBus Controller [4372]" -r11 "Hewlett-Packard Company [103c]" "Device [309b]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 IDE Controller [4376]" -p8a "Hewlett-Packard Company [103c]" "Device [309b]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-ISA Bridge [4377]" "" ""
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-PCI Bridge [4371]" -p01 "" ""
00:14.5 "Multimedia audio controller [0401]" "ATI Technologies Inc [1002]" "IXP SB400 AC'97 Audio Controller [4370]" -r02 "Hewlett-Packard Company [103c]" "Device [309b]"
00:14.6 "Modem [0703]" "ATI Technologies Inc [1002]" "SB400 AC'97 Modem Controller [4378]" -r02 "Hewlett-Packard Company [103c]" "Device [309b]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Radeon XPRESS 200M 5955 (PCIE) [5955]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:02.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Hewlett-Packard Company [103c]" "Device [1355]"
06:04.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx21/x515 Cardbus Controller [8031]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:04.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "OHCI Compliant IEEE 1394 Host Controller [8032]" -p10 "Hewlett-Packard Company [103c]" "Device [309b]"
06:04.3 "Mass storage controller [0180]" "Texas Instruments [104c]" "PCIxx21 Integrated FlashMedia Controller [8033]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:04.4 "SD Host controller [0805]" "Texas Instruments [104c]" "PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [8034]" "Hewlett-Packard Company [103c]" "Device [309b]"
06:06.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Hewlett-Packard Company [103c]" "Device [309b]"


I have tried ndiswrapper and now am using the firmwre included in the hardware driver menu both with no luck.

If you having already tried the following (I am assuming that you are using the b43 driver since you mentioned firmware):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo depmod -a
sudo modprobe b43
sudo /etc/init.d/networking restart
```and it does not work, you will most likely have to stick with ndiswrapper.

---

### Post by Ayuthia on 2008-11-01
> **oosh50 said:**
> none of the above worked for me  (asus x50r ubuntu 8.10 BCM4311) wireless light goes off when login screen loads, broadcom STA drivers dont work!

Can you let me know which revision of the 4311 card you have:
```
lspci -nn
```

Also, do you have an internet connection in Ubuntu?  You might have to try the b43 driver if you have the 4311 rev 02 card.

---

### Post by Angelbeast on 2008-11-01
> **Ayuthia said:**
> If you having already tried the following (I am assuming that you are using the b43 driver since you mentioned firmware):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo depmod -a
sudo modprobe b43
sudo /etc/init.d/networking restart
```and it does not work, you will most likely have to stick with ndiswrapper.

Sadly ndiswrapper was not working either..I have tried B43 in the restricted drivers manager and ndiswrapper several times each and no luck. Does anyone else have any other ideas?  This is why i keep going to other distros *LOL*

---

### Post by kolibri on 2008-11-02
> **Ayuthia said:**
> 

Your lshw information looks like you should be using the wl driver.  Please try the following (It should not matter if you are upgrading or if it is a fresh install):
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
```

Thank you.  I did a clean install (to try to undo anything weird I corrupted in previous attempts) , and entered the code above, and one of those things worked.

The good thing about 8.10- my Nvidia card worked right from the get go for the first time.

---

### Post by oosh50 on 2008-11-02
I do have a wired Internet connection also re-installed ubuntu and sta drivers till no luck, it detects the wireless networks but no network light on laptop still, i've tried the b43 before but no luck.

```
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
06:00.0 Ethernet controller [0200]: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter [1969:2048] (rev a0)

```

any ideas???

---

### Post by Ayuthia on 2008-11-02
> **oosh50 said:**
> I do have a wired Internet connection also re-installed ubuntu and sta drivers till no luck, it detects the wireless networks but no network light on laptop still, i've tried the b43 before but no luck.

```
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
06:00.0 Ethernet controller [0200]: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter [1969:2048] (rev a0)

```

any ideas???

We have the same card so it should work with either the b43 or the STA (wl) version.  Can you show me the results of:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
lsmod|grep -e b4 -e ssb -e ndis -e wl
lshw -C network
dmesg|grep 'wl '
```

---

### Post by guycross on 2008-11-02
followed the setps in point #2 and wifi is working on my dell inspiron 1520 with broadcom 43xx wifi card

many thanks

i owe yall a beer
Guy
[email]guy@sleepywhisper.com[/email]

---

### Post by Luk_Deisler on 2008-11-02
> **Ayuthia said:**
> You will need to use the b43 module instead of the wl module.  The Broadcom STA (wl) module does not work with the 4318 cards.  You will need a wired connection in Ubuntu if you want to activate that module or else install b43-fwcutter.  If you don't have a connection in Ubuntu, you can try the information in post #72:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
It contains instructions on how to download the necessary files from another computer (or through Windows if you are dual-booting) to get the b43 modules working in Ubuntu.

Thank you mate, works like a charm now :)

---

### Post by oosh50 on 2008-11-02
this is what i got:

```
nick@toplap-n-syuch:~$ sudo modprobe -r b43 ssb ndiswrapper wl
[sudo] password for nick: 
nick@toplap-n-syuch:~$ sudo modprobe wl
nick@toplap-n-syuch:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
nick@toplap-n-syuch:~$ lsmod|grep -e b4 -e ssb -e ndis -e wl
wl                   1076372  0 
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip
nick@toplap-n-syuch:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:8c:0a:19:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:96:8b:1c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 module=atl2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:6d:b1:9b:9d:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nick@toplap-n-syuch:~$ dmesg|grep 'wl '
[   14.657937] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.657946] wl 0000:02:00.0: setting latency timer to 64
[  282.856194] wl 0000:02:00.0: PCI INT A disabled
[  291.187475] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  291.187508] wl 0000:02:00.0: setting latency timer to 64
nick@toplap-n-syuch:~$ 
```

---

### Post by Ayuthia on 2008-11-02
> **oosh50 said:**
> this is what i got:

```
nick@toplap-n-syuch:~$ sudo modprobe -r b43 ssb ndiswrapper wl
[sudo] password for nick: 
nick@toplap-n-syuch:~$ sudo modprobe wl
nick@toplap-n-syuch:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
nick@toplap-n-syuch:~$ lsmod|grep -e b4 -e ssb -e ndis -e wl
wl                   1076372  0 
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip
nick@toplap-n-syuch:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:8c:0a:19:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:96:8b:1c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 module=atl2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:6d:b1:9b:9d:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
nick@toplap-n-syuch:~$ dmesg|grep 'wl '
[   14.657937] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.657946] wl 0000:02:00.0: setting latency timer to 64
[  282.856194] wl 0000:02:00.0: PCI INT A disabled
[  291.187475] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  291.187508] wl 0000:02:00.0: setting latency timer to 64
nick@toplap-n-syuch:~$ 
```

Let's see if we can get it to turn on by doing the following (I am putting the previous steps back in just in case you rebooted):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

---

### Post by oosh50 on 2008-11-02
hmm still not working

```
nick@toplap-n-syuch:~$ sudo modprobe -r b43 ssb ndiswrapper wl
[sudo] password for nick: 
nick@toplap-n-syuch:~$ sudo modprobe wl
nick@toplap-n-syuch:~$ sudo ifconfig eth1 up
nick@toplap-n-syuch:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

nick@toplap-n-syuch:~$ 

```

---

### Post by arnarg on 2008-11-02
> **oosh50 said:**
> none of the above worked for me  (asus x50r ubuntu 8.10 BCM4311) wireless light goes off when login screen loads, broadcom STA drivers dont work!

I have the exact same type and the led for the wireless turns off to and if you turn off and then turn on again with the switch on the side it turns on for a split second and the turns off again :S

---

### Post by arnarg on 2008-11-02
> **Ayuthia said:**
> You might try the following since you had ndiswrapper in the previous version:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart

```I am thinking that there is a chance that the ndiswrapper driver is causing a conflict.  I have the same card as you and it took a little work but I was able to get it running when I was using the live CD.  I was using the wl driver with my installed version of Intrepid and it updated without issue.  Hopefully yours will work as well.

didn't see any changes... :S
But I have the same laptop as oosh50 so it's probably the same problem.

---

### Post by Pizbit on 2008-11-02
Cheers Ayuthia, your post got me up and running in minutes.
I was tracking the thread for a post just like yours before installing ;)

Here's the lspci output for my laptop's wireless.

00:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [120f]"

er, sleepy, and I be meaning the post on page 8, #72 ;)
[http://ge.ubuntuforums.com/showpost.php?p=6077792&postcount=72](http://ge.ubuntuforums.com/showpost.php?p=6077792&postcount=72)

---

### Post by brandoncolorado on 2008-11-02
I have a friend with this 4318 card.  He updated to 8.10 (wireless was working in 8.04).  Is this problem ever going to be fixed automatically by an update, or is this something that won't be fixed?  He is a linux beginner, and the instructions in this thread are a little mind boggling.

---

### Post by springs015 on 2008-11-02
I am having similar problems, 
Broadcom Corporation BCM4312 802.11b/g (rev 01)
0b:00.0 0280: 14e4:4315 (rev 01)

Manufacturer: 	Broadcom Corp.
Chipset Family Type: 	802.11 Wireless LAN
Chipset Family: 	BCM43xx 802.11abg WLAN  Dual-Band
Chipset: 	BCM4312 WLAN-abg MiniCard 

I am trying to install firmware for my network card.

I tryed to install the firmware through the terminal but it wouldn't work, then I installed b43-fwcutter through synaptic and then ran it in the terminal. 
[B]

lspci -nn[/B]
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

**lshw -C network**
```
 *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d0:a3:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:05:6a:d0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.5 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:ee:24:d3:ed:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 
```

I followed the instructions in post 72 by Ayuthia, and it was going fine until


 
```
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
Cannot open input file --unsuported

```


been trying to figure this out for awhile any input would be appreciated.

---

### Post by Pizbit on 2008-11-02
> **springs015 said:**
> ```
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
Cannot open input file --unsuported

```


been trying to figure this out for awhile any input would be appreciated.

Spelling of unsupported. :)

(I did the same mistake heh)

---

### Post by springs015 on 2008-11-02
> **Pizbit said:**
> Spelling of unsupported. :)

(I did the same mistake heh)

opps, I hate missing stuff like that ... well i re-entered it and got this error instead : (
-```
stefan@stefan-laptop:~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta.mimo.o
Cannot open input file broadcom-wl-4.150.10.5/driver/wl_apsta.mimo.o

```

---

### Post by ganooch on 2008-11-02
[SIZE="4"]Wow, I have been at this all afternoon with no luck.  As far as I can tell, I have a generic driver from ndiswrapper and the 4318 adapter.  I am new at this and have tried everything in this thread to no avail.  Is it that I don't know how to set my encryption key (WPA2)?  I used to use wicd in 8.04, that is not here now.  Now I right-click on the network connection logo on the top right and enter my key.  Each time I go to edit it, it is something different from what I have put in.  Anyway, my info is below and I would love any assistance at all.[/SIZE]

```
Output from my attempts of Post #72:
chris@chris-laptop:/etc/init.d$ cd /home/
chris@chris-laptop:/home$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
chris@chris-laptop:/home$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
broadcom-wl-4.150.10.5/
tar: broadcom-wl-4.150.10.5: Cannot mkdir: Permission denied
broadcom-wl-4.150.10.5/driver/
tar: broadcom-wl-4.150.10.5/driver: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/driver/config/
tar: broadcom-wl-4.150.10.5/driver/config: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_apdef
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_apdef: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap_1chipG
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap_1chipG: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap_micro
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap_micro: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap_mimo
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_ap_mimo: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta_1chipG
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta_1chipG: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta_micro
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta_micro: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta_mimo
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_apsta_mimo: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta_1chipG
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta_1chipG: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta_micro
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta_micro: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta_mimo
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_router_sta_mimo: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_shared
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_lx_shared: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_micro
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_micro: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wlconfig_nomimo
tar: broadcom-wl-4.150.10.5/driver/config/wlconfig_nomimo: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wl_default
tar: broadcom-wl-4.150.10.5/driver/config/wl_default: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/config/wl_hnd
tar: broadcom-wl-4.150.10.5/driver/config/wl_hnd: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_ap_micro.o
tar: broadcom-wl-4.150.10.5/driver/wl_ap_micro.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_ap_mimo.o
tar: broadcom-wl-4.150.10.5/driver/wl_ap_mimo.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_ap.o
tar: broadcom-wl-4.150.10.5/driver/wl_ap.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_apsta_micro.o
tar: broadcom-wl-4.150.10.5/driver/wl_apsta_micro.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
tar: broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_apsta.o
tar: broadcom-wl-4.150.10.5/driver/wl_apsta.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_sta_micro.o
tar: broadcom-wl-4.150.10.5/driver/wl_sta_micro.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_sta_mimo.o
tar: broadcom-wl-4.150.10.5/driver/wl_sta_mimo.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/driver/wl_sta.o
tar: broadcom-wl-4.150.10.5/driver/wl_sta.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/nas_exe.o
tar: broadcom-wl-4.150.10.5/nas_exe.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/wl_exe.o
tar: broadcom-wl-4.150.10.5/wl_exe.o: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/
tar: broadcom-wl-4.150.10.5/include: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/include/UdpLib.h
tar: broadcom-wl-4.150.10.5/include/UdpLib.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcm4710.h
tar: broadcom-wl-4.150.10.5/include/bcm4710.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcm947xx.h
tar: broadcom-wl-4.150.10.5/include/bcm947xx.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/
tar: broadcom-wl-4.150.10.5/include/bcmcrypto: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/aes.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/aes.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/aeskeywrap.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/aeskeywrap.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/bcmccx.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/bcmccx.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/bn.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/bn.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/ccx.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/ccx.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/des.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/des.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/dh.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/dh.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/hmac_sha256.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/hmac_sha256.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/md4.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/md4.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/md5.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/md5.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/passhash.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/passhash.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/prf.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/prf.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/rc4.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/rc4.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/rijndael-alg-fst.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/rijndael-alg-fst.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/sha1.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/sha1.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmcrypto/sha256.h
tar: broadcom-wl-4.150.10.5/include/bcmcrypto/sha256.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmdefs.h
tar: broadcom-wl-4.150.10.5/include/bcmdefs.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmdevs.h
tar: broadcom-wl-4.150.10.5/include/bcmdevs.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmendian.h
tar: broadcom-wl-4.150.10.5/include/bcmendian.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmnvram.h
tar: broadcom-wl-4.150.10.5/include/bcmnvram.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmotp.h
tar: broadcom-wl-4.150.10.5/include/bcmotp.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmparams.h
tar: broadcom-wl-4.150.10.5/include/bcmparams.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmperf.h
tar: broadcom-wl-4.150.10.5/include/bcmperf.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmrobo.h
tar: broadcom-wl-4.150.10.5/include/bcmrobo.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmsrom.h
tar: broadcom-wl-4.150.10.5/include/bcmsrom.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmstdlib.h
tar: broadcom-wl-4.150.10.5/include/bcmstdlib.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmutils.h
tar: broadcom-wl-4.150.10.5/include/bcmutils.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bcmwifi.h
tar: broadcom-wl-4.150.10.5/include/bcmwifi.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/bitfuncs.h
tar: broadcom-wl-4.150.10.5/include/bitfuncs.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/epivers.h
tar: broadcom-wl-4.150.10.5/include/epivers.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/epivers.h.in
tar: broadcom-wl-4.150.10.5/include/epivers.h.in: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/etioctl.h
tar: broadcom-wl-4.150.10.5/include/etioctl.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/flash.h
tar: broadcom-wl-4.150.10.5/include/flash.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/flashutl.h
tar: broadcom-wl-4.150.10.5/include/flashutl.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hndchipc.h
tar: broadcom-wl-4.150.10.5/include/hndchipc.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hndcpu.h
tar: broadcom-wl-4.150.10.5/include/hndcpu.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hnddma.h
tar: broadcom-wl-4.150.10.5/include/hnddma.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hndgige.h
tar: broadcom-wl-4.150.10.5/include/hndgige.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hndmips.h
tar: broadcom-wl-4.150.10.5/include/hndmips.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hndpci.h
tar: broadcom-wl-4.150.10.5/include/hndpci.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/hndpmu.h
tar: broadcom-wl-4.150.10.5/include/hndpmu.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/linux_gpio.h
tar: broadcom-wl-4.150.10.5/include/linux_gpio.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/linuxver.h
tar: broadcom-wl-4.150.10.5/include/linuxver.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/min_osl.h
tar: broadcom-wl-4.150.10.5/include/min_osl.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/mipsinc.h
tar: broadcom-wl-4.150.10.5/include/mipsinc.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/ndiserrmap.h
tar: broadcom-wl-4.150.10.5/include/ndiserrmap.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/osl.h
tar: broadcom-wl-4.150.10.5/include/osl.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/pcicfg.h
tar: broadcom-wl-4.150.10.5/include/pcicfg.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/
tar: broadcom-wl-4.150.10.5/include/proto: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/include/proto/802.11.h
tar: broadcom-wl-4.150.10.5/include/proto/802.11.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/802.11e.h
tar: broadcom-wl-4.150.10.5/include/proto/802.11e.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/802.1d.h
tar: broadcom-wl-4.150.10.5/include/proto/802.1d.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/bcmeth.h
tar: broadcom-wl-4.150.10.5/include/proto/bcmeth.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/bcmevent.h
tar: broadcom-wl-4.150.10.5/include/proto/bcmevent.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/bcmip.h
tar: broadcom-wl-4.150.10.5/include/proto/bcmip.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/bcmtcp.h
tar: broadcom-wl-4.150.10.5/include/proto/bcmtcp.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/eap.h
tar: broadcom-wl-4.150.10.5/include/proto/eap.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/eapol.h
tar: broadcom-wl-4.150.10.5/include/proto/eapol.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/ethernet.h
tar: broadcom-wl-4.150.10.5/include/proto/ethernet.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/vlan.h
tar: broadcom-wl-4.150.10.5/include/proto/vlan.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/proto/wpa.h
tar: broadcom-wl-4.150.10.5/include/proto/wpa.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/rts/
tar: broadcom-wl-4.150.10.5/include/rts: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/include/rts/crc.h
tar: broadcom-wl-4.150.10.5/include/rts/crc.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbchipc.h
tar: broadcom-wl-4.150.10.5/include/sbchipc.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbconfig.h
tar: broadcom-wl-4.150.10.5/include/sbconfig.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbgige.h
tar: broadcom-wl-4.150.10.5/include/sbgige.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbhndcpu.h
tar: broadcom-wl-4.150.10.5/include/sbhndcpu.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbhnddma.h
tar: broadcom-wl-4.150.10.5/include/sbhnddma.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbhndmips.h
tar: broadcom-wl-4.150.10.5/include/sbhndmips.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbhndpio.h
tar: broadcom-wl-4.150.10.5/include/sbhndpio.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbmemc.h
tar: broadcom-wl-4.150.10.5/include/sbmemc.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbpci.h
tar: broadcom-wl-4.150.10.5/include/sbpci.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbpcie.h
tar: broadcom-wl-4.150.10.5/include/sbpcie.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbpcmcia.h
tar: broadcom-wl-4.150.10.5/include/sbpcmcia.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbsdio.h
tar: broadcom-wl-4.150.10.5/include/sbsdio.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbsdpcmdev.h
tar: broadcom-wl-4.150.10.5/include/sbsdpcmdev.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbsdram.h
tar: broadcom-wl-4.150.10.5/include/sbsdram.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbsocram.h
tar: broadcom-wl-4.150.10.5/include/sbsocram.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbsprom.h
tar: broadcom-wl-4.150.10.5/include/sbsprom.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sbutils.h
tar: broadcom-wl-4.150.10.5/include/sbutils.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/sflash.h
tar: broadcom-wl-4.150.10.5/include/sflash.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/trxhdr.h
tar: broadcom-wl-4.150.10.5/include/trxhdr.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/typedefs.h
tar: broadcom-wl-4.150.10.5/include/typedefs.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/wlioctl.h
tar: broadcom-wl-4.150.10.5/include/wlioctl.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/include/linux_osl.h
tar: broadcom-wl-4.150.10.5/include/linux_osl.h: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/
tar: broadcom-wl-4.150.10.5/shared: Cannot mkdir: No such file or directory
broadcom-wl-4.150.10.5/shared/bcmotp.c
tar: broadcom-wl-4.150.10.5/shared/bcmotp.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/bcmrobo.c
tar: broadcom-wl-4.150.10.5/shared/bcmrobo.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/bcmsrom.c
tar: broadcom-wl-4.150.10.5/shared/bcmsrom.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/bcmstdlib.c
tar: broadcom-wl-4.150.10.5/shared/bcmstdlib.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/bcmutils.c
tar: broadcom-wl-4.150.10.5/shared/bcmutils.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/boot.S
tar: broadcom-wl-4.150.10.5/shared/boot.S: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/bzip2_inflate.c
tar: broadcom-wl-4.150.10.5/shared/bzip2_inflate.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/cfe_osl.c
tar: broadcom-wl-4.150.10.5/shared/cfe_osl.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/flashutl.c
tar: broadcom-wl-4.150.10.5/shared/flashutl.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/gzip_inflate.c
tar: broadcom-wl-4.150.10.5/shared/gzip_inflate.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hndchipc.c
tar: broadcom-wl-4.150.10.5/shared/hndchipc.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hnddma.c
tar: broadcom-wl-4.150.10.5/shared/hnddma.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hndgige.c
tar: broadcom-wl-4.150.10.5/shared/hndgige.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hndmips.c
tar: broadcom-wl-4.150.10.5/shared/hndmips.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hndpci.c
tar: broadcom-wl-4.150.10.5/shared/hndpci.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hndpmu.c
tar: broadcom-wl-4.150.10.5/shared/hndpmu.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/hndrte.lds.in
tar: broadcom-wl-4.150.10.5/shared/hndrte.lds.in: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/linux_gpio.c
tar: broadcom-wl-4.150.10.5/shared/linux_gpio.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/linux_osl.c
tar: broadcom-wl-4.150.10.5/shared/linux_osl.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/load.c
tar: broadcom-wl-4.150.10.5/shared/load.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/min_osl.c
tar: broadcom-wl-4.150.10.5/shared/min_osl.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/nvramstubs.c
tar: broadcom-wl-4.150.10.5/shared/nvramstubs.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/sbsdram.S
tar: broadcom-wl-4.150.10.5/shared/sbsdram.S: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/sbutils.c
tar: broadcom-wl-4.150.10.5/shared/sbutils.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/sflash.c
tar: broadcom-wl-4.150.10.5/shared/sflash.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/sromstubs.c
tar: broadcom-wl-4.150.10.5/shared/sromstubs.c: Cannot open: No such file or directory
broadcom-wl-4.150.10.5/shared/xip.lds.in
tar: broadcom-wl-4.150.10.5/shared/xip.lds.in: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
chris@chris-laptop:/home$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
Cannot open input file broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
chris@chris-laptop:/home$ sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
chris@chris-laptop:/home$ sudo ifconfig wlan0 up

 
```

```
lshw -C network
chris@chris-laptop:/home$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:f5:e7:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.151 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:23:bd:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wmp54gs driverversion=1.53+Linksys,12/22/2004, 3.100.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:f5:87:aa:67:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
chris@chris-laptop:/home$ 
 
```

```
lspci
chris@chris-laptop:/home$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
chris@chris-laptop:/home$ 
 
```
iwlist scan does show networks.  Shoreline Wizzay is mine...
```
chris@chris-laptop:/home$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:0A:DC:27
                    ESSID:"vavavoom_vp"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:14:6C:47:38:6C
                    ESSID:"KEEPOUT"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0C:41:D2:65:1C
                    ESSID:"richnetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:6C:EF:C4:54
                    ESSID:"CHEWDOG"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:1E:E5:39:DE:2A
                    ESSID:"Focus Today"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:1B:11:4B:FA:FD
                    ESSID:"Shoreline Wizzay"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-13 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:21:7C:7D:FE:21
                    ESSID:"2WIRE085"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:16:01:D6:C1:D5
                    ESSID:"Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

chris@chris-laptop:/home$ 
 
```

---

### Post by brandon88tube on 2008-11-02
It might start working if you do an update for 8.10, but its not guranteed. I got it to start using my wireless after that, but now it won't connect to my router.. Its just an endless cycle of whats your WEP try to connect, sorry whats your WEP..

Anyways if you can get internet somehow other than wireless for a short period of time I recommend try to update 8.10 and see if anything helps.

---

### Post by Ayuthia on 2008-11-02
> **ganooch said:**
> [SIZE="4"]Wow, I have been at this all afternoon with no luck.  As far as I can tell, I have a generic driver from ndiswrapper and the 4318 adapter.  I am new at this and have tried everything in this thread to no avail.  Is it that I don't know how to set my encryption key (WPA2)?  I used to use wicd in 8.04, that is not here now.  Now I right-click on the network connection logo on the top right and enter my key.  Each time I go to edit it, it is something different from what I have put in.  Anyway, my info is below and I would love any assistance at all.[/SIZE]


You can reinstall wicd by going to the wicd site.  It has instructions on how to install wicd in Intrepid:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by Ayuthia on 2008-11-02
> **brandon88tube said:**
> It might start working if you do an update for 8.10, but its not guranteed. I got it to start using my wireless after that, but now it won't connect to my router.. Its just an endless cycle of whats your WEP try to connect, sorry whats your WEP..

Anyways if you can get internet somehow other than wireless for a short period of time I recommend try to update 8.10 and see if anything helps.

You might try going to the Terminal and see if you can connect to your router:
```
sudo iwconfig wlan0 essid router-name key passkey
sudo dhclient wlan0
```
Just replace router-name with the name of the router that you are trying to connect and replace passkey with the password.  If your wireless is eth1 replace wlan0 with eth1.

---

### Post by Ayuthia on 2008-11-02
> **springs015 said:**
> opps, I hate missing stuff like that ... well i re-entered it and got this error instead : (
-```
stefan@stefan-laptop:~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta.mimo.o
Cannot open input file broadcom-wl-4.150.10.5/driver/wl_apsta.mimo.o

```

It looks like you might be in the wrong directory.  However, I am going to stop you right there.  You have a 14e4:4315 card which is not supported by they b43 driver at this time.  Your current options are ndiswrapper and the Broadcom STA (wl) driver.  You should try the Broadcom STA option first.  If you have problems with it, please come back and let us know what is happening.

---

### Post by brandon88tube on 2008-11-02
> **Ayuthia said:**
> You might try going to the Terminal and see if you can connect to your router:
```
sudo iwconfig wlan0 essid router-name key passkey
sudo dhclient wlan0
```
Just replace router-name with the name of the router that you are trying to connect and replace passkey with the password.  If your wireless is eth1 replace wlan0 with eth1.

I'll have to give that a try later and see how it works. I'll post back with the results. I also tried to update the first post to help those new to the thread. Any advice on improving it would be great.

---

### Post by Ayuthia on 2008-11-02
> **arnarg said:**
> didn't see any changes... :S
But I have the same laptop as oosh50 so it's probably the same problem.

arnarg and oosh50 - Can you both post the results of lspci -knnmvd 14e4:*

I am trying to see where your card differs from mine.  You both might want to try the b43 driver.  It should work as well as the Broadcom STA driver but it requires the firmware download.  If you don't have a working connection in Ubuntu, try using the instructions in post #72:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by brandon88tube on 2008-11-02
Ok, this is what I got when I tried to connect through the terminal. Still can't connect.

```
brandon@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:4e:39:74
Sending on   LPF/wlan0/00:14:a5:4e:39:74
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by arnarg on 2008-11-02
> **Ayuthia said:**
> arnarg and oosh50 - Can you both post the results of lspci -knnmvd 14e4:*

I am trying to see where your card differs from mine.  You both might want to try the b43 driver.  It should work as well as the Broadcom STA driver but it requires the firmware download.  If you don't have a working connection in Ubuntu, try using the instructions in post #72:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

Here you go...

> arnar@arnar-laptop:~$ lspci -knnmvd 14e4:*
Device:	02:00.0
Class:	Network controller [0280]
Vendor:	Broadcom Corporation [14e4]
Device:	BCM4311 802.11b/g WLAN [4311]
SVendor:	ASUSTeK Computer Inc. [1043]
SDevice:	Device [170f]
Rev:	01
Driver:	wl
Module:	ssb
Module:	wl

In 8.04 the STA driver worked much better.


EDIT:
I installed b43-fwcutter using the instructions you linked but still I can't connect...

---

### Post by oosh50 on 2008-11-02
```
lspci -knnmvd 14e4:*










nick@toplap-n-syuch:~$ lspci -knnvd 14e4:*
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:170f]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa9fc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb




```
i also installed the b43-fwcutter and it didnt work

---

### Post by Ayuthia on 2008-11-02
> **arnarg said:**
> Here you go...



In 8.04 the STA driver worked much better.


EDIT:
I installed b43-fwcutter using the instructions you linked but still I can't connect...

oosh50 and arnarg: Try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo /etc/init.d/networking restart
sudo iwlist scan
```

Just in case, can you double-check and make sure that the wireless switch is on (if there is one)?  I am guessing that it is because the both of you have the same issue along with the same card.

---

### Post by ganooch on 2008-11-02
> **Ayuthia said:**
> You can reinstall wicd by going to the wicd site.  It has instructions on how to install wicd in Intrepid:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)


That did the trick,  Network manager was not doing the job and wicd worked like a charm.  You are the man and I owe you a beer when you are in the Dallas area, PM me.

---

### Post by arnarg on 2008-11-02
> **Ayuthia said:**
> oosh50 and arnarg: Try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo /etc/init.d/networking restart
sudo iwlist scan
```

Just in case, can you double-check and make sure that the wireless switch is on (if there is one)?  I am guessing that it is because the both of you have the same issue along with the same card.

It didn't work :S I double-checked the switch, it's on. But ever since I upgraded to 8.10 the wireless lan LED turns off after the ubuntu boot screen.

---

### Post by Ayuthia on 2008-11-02
> **arnarg said:**
> It didn't work :S I double-checked the switch, it's on. But ever since I upgraded to 8.10 the wireless lan LED turns off after the ubuntu boot screen.

Can you do one more thing for me?  I would like to see the information from:
```
dmesg|grep b43
lsmod
```Thanks.

---

### Post by gopchandani on 2008-11-02
Hello All,

I tried 8.10 today and it came in (I had to enable the driver as soon as Ubuntu installation finished, which I did) with my wireless card's (Broadcomm 4310 chip, Intel Card) drivers so didn't have to go with the popular hacks for using Windows drivers.

However, I got stuck with the same problem which I got stuck with 8.04, i.e. I am still not able to connect to WPA encrypted home network. However, I can connect to unencrypted wifi connections.

Is it a known issue with 8.10? If so, what is the fix?

Please help out!


Rakesh

---

### Post by mngt on 2008-11-02
```
sudo modprobe -r b43 b44 ssb wl

sudo modprobe ieee80211_crypt_tkip

sudo modprobe wl

sudo modprobe b44

sudo /etc/init.d/networking restart
```

this works for me. But everything I reboot my system, it requires me to do it again and again. Can someone tell me how i can fix this? 

Thanks.

---

### Post by arnarg on 2008-11-03
> **Ayuthia said:**
> Can you do one more thing for me?  I would like to see the information from:
```
dmesg|grep b43
lsmod
```Thanks.

okay.

> arnar@arnar-laptop:~$ dmesg|grep b43
[    4.687757] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.687777] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   19.373173] b43-phy0: Broadcom 4311 WLAN found
[   34.513665] input: b43-phy0 as /devices/virtual/input/input9
[   34.636109] firmware: requesting b43/ucode5.fw
[   34.736933] firmware: requesting b43/pcm5.fw
[   34.744278] firmware: requesting b43/b0g0initvals5.fw
[   34.777561] firmware: requesting b43/b0g0bsinitvals5.fw
[   34.908134] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   35.077040] Registered led device: b43-phy0::tx
[   35.078880] Registered led device: b43-phy0::rx
[   35.079383] Registered led device: b43-phy0::radio
[   35.548129] b43-phy0: Radio hardware status changed to DISABLED
[   96.741326] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[  103.346560] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  103.346582] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[  103.473778] b43-phy0: Broadcom 4311 WLAN found
[  107.601796] input: b43-phy0 as /devices/virtual/input/input10
[  107.701069] firmware: requesting b43/ucode5.fw
[  107.703727] firmware: requesting b43/pcm5.fw
[  107.707087] firmware: requesting b43/b0g0initvals5.fw
[  107.711370] firmware: requesting b43/b0g0bsinitvals5.fw
[  107.832091] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  108.001447] Registered led device: b43-phy0::tx
[  108.001508] Registered led device: b43-phy0::rx
[  108.001557] Registered led device: b43-phy0::radio
[  108.624097] b43-phy0: Radio hardware status changed to DISABLED

> arnar@arnar-laptop:~$ lsmod

Module                  Size  Used by

ipv6                  263972  10 

b43                   131356  0 

ssb                    40580  1 b43

mac80211              216820  1 b43

cfg80211               32392  1 mac80211

input_polldev          11912  1 b43

af_packet              25728  2 

rfkill_input           12672  0 

binfmt_misc            16904  1 

rfcomm                 44432  0 

bridge                 56980  0 

stp                    10628  1 bridge

bnep                   20480  2 

sco                    18308  2 

l2cap                  30464  6 rfcomm,bnep

bluetooth              61924  6 rfcomm,bnep,sco,l2cap

ppdev                  15620  0 

acpi_cpufreq           15500  0 

cpufreq_userspace      11396  0 

cpufreq_stats          13188  0 

cpufreq_powersave       9856  0 

cpufreq_ondemand       14988  2 

freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand

cpufreq_conservative    14600  0 

wmi                    14504  0 

sbs                    19464  0 

sbshc                  13440  1 sbs

pci_slot               12552  0 

container              11520  0 

iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables

parport_pc             39204  0 

lp                     17156  0 

parport                42604  3 ppdev,parport_pc,lp

joydev                 18368  0 

arc4                    9984  2 

evdev                  17696  11 

ecb                    10880  2 

crypto_blkcipher       25476  1 ecb

snd_hda_intel         381488  3 

psmouse                45200  0 

pcspkr                 10624  0 

serio_raw              13444  0 

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss

rfkill                 17176  3 b43,rfkill_input

snd_seq_dummy          10884  0 

snd_seq_oss            38528  0 

snd_seq_midi           14336  0 

snd_rawmidi            29824  1 snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

ac                     12292  0 

battery                18436  0 

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

video                  25104  0 

output                 11008  1 video

atl2                   34072  0 

fglrx                1813960  27 

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

asus_laptop            24440  0 

i2c_piix4              16144  0 

snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

button                 14224  0 

soundcore              15328  1 snd

led_class              12164  2 b43,asus_laptop

i2c_core               31892  1 i2c_piix4

snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

ati_agp                14988  0 

agpgart                42184  2 fglrx,ati_agp

shpchp                 37908  0 

pci_hotplug            35236  1 shpchp

ext2                   72456  1 

mbcache                16004  1 ext2

sr_mod                 22212  0 

cdrom                  43168  1 sr_mod

usb_storage            81728  0 

sd_mod                 42264  3 

crc_t10dif              9984  1 sd_mod

pata_atiixp            12800  0 

sg                     39732  0 

pata_acpi              12160  0 

libusual               27156  1 usb_storage

ata_generic            12932  0 

ahci                   37132  2 

ehci_hcd               43276  0 

libata                177312  4 pata_atiixp,pata_acpi,ata_generic,ahci

scsi_mod              155212  5 sr_mod,usb_storage,sd_mod,sg,libata

dock                   16656  1 libata

ohci_hcd               31888  0 

usbcore               148848  5 usb_storage,libusual,ehci_hcd,ohci_hcd

thermal                23708  0 

processor              42156  4 acpi_cpufreq,thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  3 


ADD:
[solved] Just installed wicd, that did the trick :) At least working so far...
Thanks for all the help guys.

---

### Post by DemonWasp on 2008-11-03
[WORKING] - I got my chipset to work. I'm on a Dell 1505N wireless card (**BCM 4328 chipset**). The following instructions allow both the wired and wireless connections to work:

```

#! /bin/sh
sudo modprobe -r wl     # Unload the WL driver
sudo modprobe -r b44    # Unload the BCM 44xx driver (runs the wired card, you WILL lose your connection
sudo modprobe -r ssb    # Unload the required base for the b44 driver, which is holding our wireless hostage
sudo modprobe wl        # Reload WL driver first, rescuing our wireless
sudo modprobe ssb       # Now bring back ssb, so that we can...
sudo modprobe b44       # Bring back our wired driver, so we have both!

```

This appears to be a problem with ssb grabbing control of the wireless card as well as the wired card, when it should only be grabbing the wired card.

---

### Post by brandon88tube on 2008-11-03
In my previous post I tried connecting through the terminal and posted the output. I tried to connect again and I realized that when I select WEP 128-bit Passphrase it defaults back to WEP 48/128-bit and then I select to show the key, but it ends up being this completely different key then what I had typed in. Maybe this is the cause.

---

### Post by Ayuthia on 2008-11-03
> **mngt said:**
> ```
sudo modprobe -r b43 b44 ssb wl

sudo modprobe ieee80211_crypt_tkip

sudo modprobe wl

sudo modprobe b44

sudo /etc/init.d/networking restart
```

this works for me. But everything I reboot my system, it requires me to do it again and again. Can someone tell me how i can fix this? 

Thanks.

If you copy that information and remove the sudo command, you can put them into /etc/rc.local:
```
gksu gedit/etc/rc.local
```
Add at the end of the file:
```
modprobe -r b43 b44 ssb wl
modprobe ieee80211_crypt_tkip
modprobe wl
modprobe b44
/etc/init.d/networking restart
```

---

### Post by Ayuthia on 2008-11-03
> **brandon88tube said:**
> In my previous post I tried connecting through the terminal and posted the output. I tried to connect again and I realized that when I select WEP 128-bit Passphrase it defaults back to WEP 48/128-bit and then I select to show the key, but it ends up being this completely different key then what I had typed in. Maybe this is the cause.

You might try wicd.  It sometimes works better than Network manager.
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
There are instructions in the link on how to install it.

---

### Post by brandon88tube on 2008-11-03
This is really discouraging... I really don't feel like installing wicd. :(

---

### Post by oosh50 on 2008-11-03
I've tried everything including using wicd and nothing seems to work, i can detect networks but cant join and still no wireless light at all

---

### Post by raknahsamu on 2008-11-03
> **Ayuthia said:**
> Sorry.  Can you try the following:
```
sudo modprobe -r b43 ssb bcm43xx wl
sudo depmod -a
sudo modprobe wl
sudo /etc/init.d/networking restart
```

Hopefully that will get it started.  If it does, then we will need to blacklist the b43 and ssb modules.  I will try to download the Intrepid CD and see if I can duplicate this issue (I have been upgrading since the alpha stages).
Hi!

I am getting a fatal error message

"FATAL: Module ssb is in use." when I run sudo modprobe -r b43 ssb bcm43xx wl

I am using Broadcom BCM4318.

Any thoughts on how to fix this would be greatly appreciated.

Regards,
raknahsamu

---

### Post by brandoncolorado on 2008-11-03
Hey everyone,

I have some helpful insight.  My friend has the BCM 4318.  We had the same trouble after an upgrade to 8.10.  The restricted driver was installed, but there were no networks showing up.  However, we finally found out that the only networks that were not showing up were WEP or WPA secured networks.  This made it seem as though the wireless card was not finding any networks.  When the laptop was introduced to an unsecured network, the networks showed up in network manager.  Hope that helps.

---

### Post by brandon88tube on 2008-11-03
I hope they come out with some updates for 8.10 soon that fix some of the problems that people have been having.

---

### Post by Ayuthia on 2008-11-03
> **raknahsamu said:**
> Hi!

I am getting a fatal error message

"FATAL: Module ssb is in use." when I run sudo modprobe -r b43 ssb bcm43xx wl

I am using Broadcom BCM4318.

Any thoughts on how to fix this would be greatly appreciated.

Regards,
raknahsamu

It sounds like you might have the b44 driver for your wired.  You might try:
```
sudo modprobe -r b43 b44 ssb wl
```

Once you have your wireless driver loaded, you will need to load back b44:
```
sudo modprobe b44
sudo ifconfig eth0 up
```
Or else your wired connection will not come back up (until you restart).

---

### Post by scamper_22 on 2008-11-03
I can never understand Ubuntu wireless.

Everytime I update distros, wireless breaks.
Then it's a mission for a few days of running through forums and ndiswrapper and installing and uninstalling and trying every kind of script.

Then suddenly, out of nowhere a pointless reboot and it works.  I can't figure it out.  I'm almost scared to upgrade again.

Well somehow it worked out again.  No idea how.
BTW, I am using wifi-radar to choose my network.  Is there a network scanner as part of the new network manager.  As far as I can see, it only has manual entries?

---

### Post by brandon88tube on 2008-11-04
Well I have no idea why, but my wireless for some reason is now working. I decided to try and connect online through the ethernet and see if there were any updates for 8.10. No updates, so I figured what the heck, I'll try wireless again. What do you know it worked. I have no idea what happened.

---

### Post by alexh3791 on 2008-11-04
> **DemonWasp said:**
> [WORKING] - I got my chipset to work. I'm on a Dell 1505N wireless card (**BCM 4328 chipset**). The following instructions allow both the wired and wireless connections to work:

```

#! /bin/sh
sudo modprobe -r wl     # Unload the WL driver
sudo modprobe -r b44    # Unload the BCM 44xx driver (runs the wired card, you WILL lose your connection
sudo modprobe -r ssb    # Unload the required base for the b44 driver, which is holding our wireless hostage
sudo modprobe wl        # Reload WL driver first, rescuing our wireless
sudo modprobe ssb       # Now bring back ssb, so that we can...
sudo modprobe b44       # Bring back our wired driver, so we have both!

```

This appears to be a problem with ssb grabbing control of the wireless card as well as the wired card, when it should only be grabbing the wired card.

I tried to get this to work, but I keep running into a fatal error when I try to remove "ssb". It says that it is in use and I do not know how to shut it down. Any suggestions?

---

### Post by Ayuthia on 2008-11-04
> **alexh3791 said:**
> I tried to get this to work, but I keep running into a fatal error when I try to remove "ssb". It says that it is in use and I do not know how to shut it down. Any suggestions?

You might want to check:
```
lsmod|grep ssb
```
It will show which modules are currently using ssb.  From there, you can figure out what you need to remove.

---

### Post by raknahsamu on 2008-11-04
> **Ayuthia said:**
> It sounds like you might have the b44 driver for your wired.  You might try:
```
sudo modprobe -r b43 b44 ssb wl
```

Once you have your wireless driver loaded, you will need to load back b44:
```
sudo modprobe b44
sudo ifconfig eth0 up
```
Or else your wired connection will not come back up (until you restart).
Ayuthia,

Cannot thank you enough for your support. I was able to connect to internet thru wireless. 

Posting this message through wireless...

Thank you! Thank you! Thank you!

---

### Post by trescott3 on 2008-11-06
I got my BCM94311 wireless card working on an HP DV6000 laptop using the guide here:

[http://trentscott.org/?p=1]("http://trentscott.org/?p=1")

---

### Post by brandon88tube on 2008-11-06
Well it seems that for some people, the problem has been fixed, which is good. So keep posting what worked for you to help those less fortunate try and get their wireless up and working.

---

### Post by Scott-271 on 2008-11-06
I was finally able to get my tower hooked up with a wired connection, and updated. That seemed to do the trick - bcm4318, btw.

I don't have any security set up (very rural area), so I can't say whether I'd have problems with that; but it picks up my signal and my neighbor's just fine.

Scott

---

### Post by alexh3791 on 2008-11-07
These are the steps I used to get my wireless working! :lolflag: (A GIANT thanks to DemonWasp and Ayuthia !)
> **DemonWasp said:**
> [WORKING] - I got my chipset to work. I'm on a Dell 1505N wireless card (**BCM 4328 chipset**). The following instructions allow both the wired and wireless connections to work:

```

#! /bin/sh
sudo modprobe -r wl     # Unload the WL driver
sudo modprobe -r b44    # Unload the BCM 44xx driver (runs the wired card, you WILL lose your connection
sudo modprobe -r ssb    # Unload the required base for the b44 driver, which is holding our wireless hostage
sudo modprobe wl        # Reload WL driver first, rescuing our wireless
sudo modprobe ssb       # Now bring back ssb, so that we can...
sudo modprobe b44       # Bring back our wired driver, so we have both!

```

This appears to be a problem with ssb grabbing control of the wireless card as well as the wired card, when it should only be grabbing the wired card.

After having a small problem removing "ssb", Ayuthia informed me how to check what was using the module...

> **Ayuthia said:**
> You might want to check:
```
lsmod|grep ssb
```
It will show which modules are currently using ssb.  From there, you can figure out what you need to remove.

---

### Post by the music man on 2008-11-07
I just installed 8.10. I have a bcm43xx card (Belkin F5D7000 v1). It worked by enabling the restricted driver. But after all updates came in, I installed them and rebooted. Then the restricted driver was gone :confused:

I am not new to Ubuntu, but I am not experienced as well. Is there a solution for this?

---

### Post by 1caras on 2008-11-08
> **atomizer said:**
> Seems like I had to disable then re-enable the hardwaredriver for broadcom.
(_and reboot_)
I upgraded from 8.04
wireless works like a charm now.

lspci -nnm:
blah blah
03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Linksys [1737]" "Device [0049]"
blah blah

I basically followed all the instructions that Brandon88 followed up until this point, where I just got too frustrated and did a reboot.

Surprise surprise, wireless started working again.

I've done so much meddling with my system I can't even get the order straight, but I'll briefly try to recap. I started with a fresh 8.10 AMD64 Xubuntu install on a Comapq Presario v2000 with an AMD Turion 64. Here's what lshw -C network gives me:

>  *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 10
                serial: 00:16:36:23:18:cf
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-network:1
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb

I started with [this thread first,](http://ubuntuforums.org/showthread.php?t=190177) since it worked on my Wubi'd 8.04 Ubuntu. It didn't work this time, however, so I went [here](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGu) and went through the process here. Then I came across this thread and followed the instructions everyone (you've been a tremendous help, by the way. Thanks) posted for Brandon88tube, since he has the same wireless chip I do. This included enabling proprietary drivers. When I got to atomizer's post, I restarted for the hell of it and wireless suddenly started working.

Hopefully someone can make more sense of it than I can. But as far as I know, it might just have been a lucky combination of steps specific to my laptop.

Again, thanks to the entire community. It takes work, but it DOES work.

---

### Post by v4nilla on 2008-11-08
> **Ayuthia said:**
> For those with the 4306 or 4318 cards, can you post the lspci -nnm for your card?  It will help provide the chipset, revision, and subvendor information for your card.  From what I have seen in Hardy, it has been hit and miss for those two cards and it looks like Intrepid has gotten a little better, but there is not enough results out there yet.

I have the 4318 here are the results from lspci -nnm. I am typing this out from my other computer since I can't get to the internet from the desktop.

"Network Controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g wireless LAN Controller [4318]" -r02 Belkin [1799] "Device [7001]"

---

### Post by Bondy_uk on 2008-11-08
Ok I will be the first to admit I may be way off base here, so apologies if this is a stupid reply. 

Im using a Belkin card with the broadcom chipset and after a lot of searching, I found that all I had to do was open up Synaptic Package Manager (enter password) search for "bcm43xx-fwcutter" and install.

It extracts your chipset info, looks on the Internet for a compatible windows driver and installs, running it via ndiswrapper. After doing that I never had any trouble.

Again sorry if im way off here, just thought it might be of help :)

---

### Post by Nachoo on 2008-11-09
Hi there, 

I'm about going crazy. I have a Dell 1420 with wireless card 1395, i just did a fresh install of 8.10, and everything is great but I can't get any webpages or email. I do connect to a wireless or wired connection but it just won't go. I thought it could be a drivers thing and installed ndiswrapper and tried a bunch of things all I got was to make the network wireless connection unstable and still no success. 

Please can someone help? In case it helps here go the outputs of lspci and lshw -C network. Really really appreciatte your help.

```
nacho@nach:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

nacho@nach:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:d3:11:2c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:ce:08:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.1.35 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:0c:ea:c2:a7:96
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by Ayuthia on 2008-11-10
> **Nachoo said:**
> Hi there, 

I'm about going crazy. I have a Dell 1420 with wireless card 1395, i just did a fresh install of 8.10, and everything is great but I can't get any webpages or email. I do connect to a wireless or wired connection but it just won't go. I thought it could be a drivers thing and installed ndiswrapper and tried a bunch of things all I got was to make the network wireless connection unstable and still no success. 

Please can someone help? In case it helps here go the outputs of lspci and lshw -C network. Really really appreciatte your help.

```
nacho@nach:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

nacho@nach:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:d3:11:2c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:ce:08:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.1.35 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:0c:ea:c2:a7:96
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

You might try the following first:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

---

### Post by Nachoo on 2008-11-10
Hey, hi! Thanks for helping!! Really really appreciate it!

```
nacho@nach:~$ sudo modprobe -r b43 b44 ssb ndiswrapper wl
[sudo] password for nacho: 
nacho@nach:~$ sudo modprobe wl
nacho@nach:~$ sudo ifconfig eth1 up
nacho@nach:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0A:E9:03:46:D8
                    ESSID:"Mary"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-41 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 02 - Address: 00:01:38:48:2B:AE
                    ESSID:"default"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-76 dBm  Noise level:-18 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:16:38:CC:8F:5C
                    ESSID:"WLAN_BA"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:16:38:EA:08:AB
                    ESSID:"WLAN_2C"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:1/5  Signal level:-84 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:16:38:EA:46:34
                    ESSID:"WLAN_B8"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:1/5  Signal level:-88 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:16:38:C4:BA:1F
                    ESSID:"Jazztel Wireless"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-16 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 07 - Address: 00:E0:98:50:A0:78
                    ESSID:"Untitled"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
```

Still not working. From the beginning I could do the scan and get the networks around. It just would not let me surf or get email, I could ping webpages, though. Trying to fix this I installed (downloading it with a different computer) ndiswrapper and a few different drivers.

I have seen an interesting post that may help me but it requires having an internet connection to do apt-get and download some other stuff, so couldn't follow it. I have access to internet through my wife's computer. The thread I talk about is: 
[HTML]http://ubuntuforums.org/showthread.php?t=859580[/HTML]

But it is also true that I can't surf when connected wired, so... maybe my problem is not a driver problem, but maybe it is now after all I did to ubuntu!!:confused:

---

### Post by SJ_tu on 2008-11-10
> **bung-foo said:**
> Heads up here, I've got a broadcom 4318 as well. All I had to do to get it to work was run synaptic, update its sources, install b43-fwcutter. have it download the firmware and reboot.

Hope that saves you some time. :-)
I have installed Ubuntu 8.10 3days back (new user from XP) and the way you said works great for my BMC4306 card.
Thanks
SJ

---

### Post by likebikes on 2008-11-10
Hi
Here's the thing. Loaded 8.10 onto my box and it found my broadcom 4306, brought up harware drivers, downloaded firmware and bingo connected to my wireless network via network manager. However, i now want to turn this box into a family server via wireless( i know wireless server not a good idea) i load 8.10 server edition and get samba going via lan. I then do sudo apt-get install bcm-fwcutter and it installs fine and picks up my 4306 as in desktop edition however i am now stuck. there appears to be no wpa_supplicant.conf how do i get a wireless connection? i have no Gui?

---

### Post by RebeccaB37 on 2008-11-10
Hello all!

I'm a little new to this so bear with me...

I have a Broadcom 4310 wireless card (apparently not supported by the linux drivers) but I have successfully followed the instructions here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) to get my wireless up and running.

However when I reboot the wireless card is deactivated and I need to run the final part of the readme instructions again

"Make available 802.11 TKIP crypto module:      
modprobe ieee80211_crypt_tkip
Insert the Broadcom wl module:                 
insmod <path>/wl.ko"

Although my network settings are remembered...

I think that this means the module is not inserting properly? Can anyone shed any light as to how I can keep the module through the boot?

Thanks!
Rebecca

---

### Post by unknown03 on 2008-11-10
Ayuthia,
thanks alot for that information. I followed your instructions and got my BCM4318 card working!

Again, thanks

---

### Post by kannedheat on 2008-11-10
Hi all,

I just updated to 8.10 and now my wireless isn't working. I downloaded b43-fwcutter and reinstalled.```
sudo apt-get install --reinstall b43-fwcutter
``` the blue light is light on my wireless, but Network Manager complains that wlan0 is unmanaged.  

```
lshw -C network
```
WARNING: you should run this program as super-user.                                       
  *-network:0                                                                             
       description: Network controller                                                    
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller                
       vendor: Broadcom Corporation                                                       
       physical id: 2                                                                     
       bus info: pci@0000:06:02.0                                                         
       version: 02                                                                        
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:be:ea:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.42 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:63:75:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:38:9a:42:36:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
lspci | grep Broadcom\ Corporation
```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
uname -a
```
Linux dv8000 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:be:ea:6a  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:febe:ea6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3017785 (3.0 MB)  TX bytes:273484 (273.4 KB)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3032 (3.0 KB)  TX bytes:3032 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:63:75:a6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-63-75-A6-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Help!

---

### Post by melvnatic on 2008-11-11
Does anyone know a fix for the problem Ubuntu 8.04 and 8.10 has that does not allow it to connect to encrypted networks?

---

### Post by lisandrotan on 2008-11-11
How do i detect wireless LAN thru Ubuntu? Please help...

---

### Post by Ayuthia on 2008-11-11
> **kannedheat said:**
> Hi all,

I just updated to 8.10 and now my wireless isn't working. I downloaded b43-fwcutter and reinstalled.```
sudo apt-get install --reinstall b43-fwcutter
``` the blue light is light on my wireless, but Network Manager complains that wlan0 is unmanaged.  

```
lshw -C network
```
WARNING: you should run this program as super-user.                                       
  *-network:0                                                                             
       description: Network controller                                                    
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller                
       vendor: Broadcom Corporation                                                       
       physical id: 2                                                                     
       bus info: pci@0000:06:02.0                                                         
       version: 02                                                                        
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:be:ea:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.42 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:63:75:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:38:9a:42:36:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
lspci | grep Broadcom\ Corporation
```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
uname -a
```
Linux dv8000 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:be:ea:6a  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:febe:ea6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3017785 (3.0 MB)  TX bytes:273484 (273.4 KB)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3032 (3.0 KB)  TX bytes:3032 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:63:75:a6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-63-75-A6-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Help!
Can you see any wireless sites:
```
sudo iwlist scan
```

---

### Post by Ayuthia on 2008-11-11
> **RebeccaB37 said:**
> Hello all!

I'm a little new to this so bear with me...

I have a Broadcom 4310 wireless card (apparently not supported by the linux drivers) but I have successfully followed the instructions here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) to get my wireless up and running.

However when I reboot the wireless card is deactivated and I need to run the final part of the readme instructions again

"Make available 802.11 TKIP crypto module:      
modprobe ieee80211_crypt_tkip
Insert the Broadcom wl module:                 
insmod <path>/wl.ko"

Although my network settings are remembered...

I think that this means the module is not inserting properly? Can anyone shed any light as to how I can keep the module through the boot?

Thanks!
Rebecca

The easy way would be to edit /etc/rc.local and place those commands in there (without sudo).  To edit:
```
gksu gedit /etc/rc.local
```
Add:
```

modprobe ieee80211_crypt_tkip
insmod <path>/wl.ko
```

---

### Post by xpanmanx on 2008-11-11
I've got a new Dell Mini 9 with a Broadcom 4312.  Fresh install of Intrepid with "apt-get upgrade" just a few minutes ago.

I think the outputs below show that my wireless should be going like a bat out of hell........but it ain't.

All of the APs in my vicinity are WPA2.  I can't see any of them in network manager.  If I try to connect to one of them as if it were a cloaked SSID, I am repeatedly prompted for the key.

I believe that everything's OK with the APs because the 100+ Winblows machines in my environment aren't feeling any of this pain.

I tried using ndiswrapper but it didn't work.  I tried installing b43-fwcutter and bricked an earlier Intrepid install.

Hoping for suggestions...

```
xpanmanx@mini9-intrepid:~$ sudo lshw -C network
[sudo] password for xpanmanx:
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:15:80:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:c2:79:34
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.14.29 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:c1:27:61:da:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
xpanmanx@mini9-intrepid:~$

```

```
xpanmanx@mini9-intrepid:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
xpanmanx@mini9-intrepid:~$
```

---

### Post by Nachoo on 2008-11-11
Hey fix it! It had nothing to do with the drivers, I had to disable the firewall in the router! Now I'm connected no problem!

Thanks!!!

---

### Post by soccerush10 on 2008-11-11
> **brandon88tube said:**
> When I go to Administration>Hardware Drivers all that comes up is the ATI driver, which I haven't enabled.
I had this same problem. You need to connect your computer directly to your router in order to get the Broadcom STA Wireless driver (System>Administration>Hardware Drivers)
This may take updating your system, which is done by System>Administration>Update Manager.
Once you get the Broadcom STA in Hardware Drivers, you can "Activate" it, which automatically downloads and installs it.  Then restart your computer to complete installation. After restart, you should have access to your wireless networks despite the fact that your Restricted Hardware Drivers utility does not display that the Broadcom STA driver is in use (this may or may not happen, it does with my laptop, which is an HP tx1320us, of the tx1000 line of HP tablet PCs). - Hope this helps :)

---

### Post by kannedheat on 2008-11-11
```
 sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```
 sudo ifconfig wlan0 up
```
```
 sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:DB:D6:65
                    ESSID:"zapper"            
                    Mode:Master               
                    Channel:6                 
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/100  Signal level:-42 dBm  Noise level=-73 dBm
                    Encryption key:on                                        
                    IE: WPA Version 1                                        
                        Group Cipher : TKIP                                  
                        Pairwise Ciphers (1) : TKIP                          
                        Authentication Suites (1) : PSK                      
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s     
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s      
                              36 Mb/s; 48 Mb/s; 54 Mb/s                      
                    Extra:tsf=000000cfacc0117a                               
                    Extra: Last beacon: 388ms ago                            
          Cell 02 - Address: 00:1C:F0:57:3E:C3                               
                    ESSID:"xbox360"                                   
                    Mode:Master                                              
                    Channel:8                                                
                    Frequency:2.447 GHz (Channel 8)                          
                    Quality=30/100  Signal level:-83 dBm  Noise level=-73 dBm
                    Encryption key:off                                       
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000004000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                  
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                 
                              48 Mb/s; 54 Mb/s                                           
                    Extra:tsf=000002810638c180                                           
                    Extra: Last beacon: 348ms ago                                        
          Cell 03 - Address: 00:14:BF:CE:AF:B7                                           
                    ESSID:"snail"                                                         
                    Mode:Master                                                          
                    Channel:11                                                           
                    Frequency:2.462 GHz (Channel 11)                                     
                    Quality=28/100  Signal level:-85 dBm  Noise level=-73 dBm            
                    Encryption key:on                                                    
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s                  
                              12 Mb/s; 48 Mb/s                                           
                    Extra:tsf=00000157894a8984                                           
                    Extra: Last beacon: 124ms ago                                        

pan0      Interface doesn't support scanning.


I can see it, and my neighbors, but I can't access it.  I do have it encrypted.

---

### Post by Ayuthia on 2008-11-12
> **kannedheat said:**
> ```
 sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```
 sudo ifconfig wlan0 up
```
```
 sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:DB:D6:65
                    ESSID:"zapper"            
                    Mode:Master               
                    Channel:6                 
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/100  Signal level:-42 dBm  Noise level=-73 dBm
                    Encryption key:on                                        
                    IE: WPA Version 1                                        
                        Group Cipher : TKIP                                  
                        Pairwise Ciphers (1) : TKIP                          
                        Authentication Suites (1) : PSK                      
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s     
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s      
                              36 Mb/s; 48 Mb/s; 54 Mb/s                      
                    Extra:tsf=000000cfacc0117a                               
                    Extra: Last beacon: 388ms ago                            
          Cell 02 - Address: 00:1C:F0:57:3E:C3                               
                    ESSID:"xbox360"                                   
                    Mode:Master                                              
                    Channel:8                                                
                    Frequency:2.447 GHz (Channel 8)                          
                    Quality=30/100  Signal level:-83 dBm  Noise level=-73 dBm
                    Encryption key:off                                       
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000004000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                  
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                 
                              48 Mb/s; 54 Mb/s                                           
                    Extra:tsf=000002810638c180                                           
                    Extra: Last beacon: 348ms ago                                        
          Cell 03 - Address: 00:14:BF:CE:AF:B7                                           
                    ESSID:"snail"                                                         
                    Mode:Master                                                          
                    Channel:11                                                           
                    Frequency:2.462 GHz (Channel 11)                                     
                    Quality=28/100  Signal level:-85 dBm  Noise level=-73 dBm            
                    Encryption key:on                                                    
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s                  
                              12 Mb/s; 48 Mb/s                                           
                    Extra:tsf=00000157894a8984                                           
                    Extra: Last beacon: 124ms ago                                        

pan0      Interface doesn't support scanning.


I can see it, and my neighbors, but I can't access it.  I do have it encrypted.

You might want to try it without encryption just to see if it works.  If it does, then we know that there is a problem with it connecting with WPA.  I have not tried using WPA yet, but some have switching over to wicd instead of network manager to get it to work.

You might also try this (if you haven't already):
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+supplicant](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+supplicant)

It is a guide on how to use WPA supplicant.

---

### Post by xpanmanx on 2008-11-12
> **xpanmanx said:**
> I've got a new Dell Mini 9 with a Broadcom 4312.  Fresh install of Intrepid with "apt-get upgrade" just a few minutes ago.

I think the outputs below show that my wireless should be going like a bat out of hell........but it ain't.

All of the APs in my vicinity are WPA2.  I can't see any of them in network manager.  If I try to connect to one of them as if it were a cloaked SSID, I am repeatedly prompted for the key.

I believe that everything's OK with the APs because the 100+ Winblows machines in my environment aren't feeling any of this pain.

I tried using ndiswrapper but it didn't work.  I tried installing b43-fwcutter and bricked an earlier Intrepid install.

Hoping for suggestions...

```
xpanmanx@mini9-intrepid:~$ sudo lshw -C network
[sudo] password for xpanmanx:
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:15:80:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:c2:79:34
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.14.29 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:c1:27:61:da:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
xpanmanx@mini9-intrepid:~$

```

```
xpanmanx@mini9-intrepid:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
xpanmanx@mini9-intrepid:~$
```

Figures.  It's working beautifully with the Dell Mini 9 Hardy image.   But Canonical tweaked out the Dell distro so that it looks a little like Winblows and that annoys me.......and God knows what else they've done to the OS.  I want to be running Intrepid right from the Canonical distro.  Is there some way for me to dissect the functonal system to figure out how to configure Intrepid?  :confused:

---

### Post by pugz3d on 2008-11-13
Just wanted to post a quick thank you to all those who attempt to help with this stuff.  I had a horrific time with a 4306 on a Latitude X300 using Hardy, but I just installed the Ibex on my D620 with a 4311 rev01, and it was buttery smooth.  STA driver offered under restricted drivers app, clicked activate, and I was up and running.  Keep up the good work.

---

### Post by bgblanch on 2008-11-13
Greetings ubuntugeeks!

I installed ubuntu 8.10 on my work laptop (shhh, don't tell my boss). It is a Dell D630 with Broadcom 4311 wireless. I activated the Broadcom wireless driver, naturally, and am able to connect while in the same room as my wireless router. However, when I move to my office (~20' and 2 walls), the connection is dropped and I am unable to connect again until I move back to the same room as the router. The laptop, in my office, is placed next to my macbook and the macbook is able to connect. Network Manager shows the signal strength at 80%. I played around with the router settings and still no joy. Is there something else I can try?

---

### Post by kannedheat on 2008-11-13
> **Ayuthia said:**
> You might want to try it without encryption just to see if it works.  If it does, then we know that there is a problem with it connecting with WPA.  I have not tried using WPA yet, but some have switching over to wicd instead of network manager to get it to work.

You might also try this (if you haven't already):
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+supplicant](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+supplicant)

It is a guide on how to use WPA supplicant.

Kmanager wasn't doing it thing, so I went to get Wicd "wicked" 
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install wic
``` After Wicd installed, I could now see my WPA connection. When I try yo connect, Authentication fails and I can't connect.

So I...
```
sudo apt-get install wpasupplicant 
```
Giving me:
Reading package lists... Done
Building dependency tree
Reading state information... Done
wpasupplicant is already the newest version.
The following packages were automatically installed and are no longer required:
  libdbus-1-qt3 libnm-glib0 openjdk-6-jdk
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by kannedheat on 2008-11-13
I then tried to connect to my WPA connection, but no go.

I've been trying to connect to my wireless, but no go

```
 route 
```                                                                              
Kernel IP routing table                                                                              
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface                        
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0                        
link-local      *               255.255.0.0     U     0      0        0 eth0                         
iwconfig                                                                                             
default         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0                        
```
iwconfig
```                                                                             
lo        no wireless extensions.                                                                    

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Zapper"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm                                                   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B             
          Power Management:off                                              
          Link Quality:0  Signal level:0  Noise level:0                     
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0          

pan0      no wireless extensions.

```
sudo iwlist
```
[sudo] password for kannedheat: 
               
lo        Interface doesn't support scanning.        

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:DB:D6:65
                    ESSID:"Zapper"            
                    Mode:Master               
                    Channel:6                 
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/100  Signal level:-66 dBm  Noise level=-73 dBm
                    Encryption key:on                                        
                    IE: WPA Version 1                                        
                        Group Cipher : TKIP                                  
                        Pairwise Ciphers (1) : TKIP                          
                        Authentication Suites (1) : PSK                      
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s     
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s      
                              36 Mb/s; 48 Mb/s; 54 Mb/s                      
                    Extra:tsf=000000f5ea61e122                               
                    Extra: Last beacon: 120ms ago                            
          Cell 02 - Address: 00:1D:7E:E8:26:A1                               
                    ESSID:"PC Serv"                                          
                    Mode:Master                                              
                    Channel:6                                                
                    Frequency:2.437 GHz (Channel 6)                          
                    Quality=30/100  Signal level:-83 dBm  Noise level=-73 dBm
                    Encryption key:on                                        
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s     
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s      
                              12 Mb/s; 48 Mb/s                               
                    Extra:tsf=000003dc88144a78                               
                    Extra: Last beacon: 404ms ago                            
          Cell 03 - Address: 00:1C:F0:57:3E:C3                               
                    ESSID:"xbox360"                                   
                    Mode:Master                                              
                    Channel:8                                                
                    Frequency:2.447 GHz (Channel 8)                          
                    Quality=35/100  Signal level:-78 dBm  Noise level=-73 dBm
                    Encryption key:off                                       
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000004000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                  
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                 
                              48 Mb/s; 54 Mb/s                                           
                    Extra:tsf=000002a73b246345                                           
                    Extra: Last beacon: 300ms ago                                        
          Cell 04 - Address: 00:1B:2F:65:31:34                                           
                    ESSID:"NETGEAR"                                                      
                    Mode:Master                                                          
                    Channel:11                                                           
                    Frequency:2.462 GHz (Channel 11)                                     
                    Quality=31/100  Signal level:-81 dBm  Noise level=-73 dBm            
                    Encryption key:on                                                    
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                  
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s                 
                              48 Mb/s; 54 Mb/s                                           
                    Extra:tsf=000009fdd60f9181                                           
                    Extra: Last beacon: 60ms ago                                         

pan0      Interface doesn't support scanning.

```
sudo lshw -C network
```
  *-network:0                       
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation                                       
       physical id: 2                                                     
       bus info: pci@0000:06:02.0                                         
       version: 02                                                        
       width: 32 bits                                                     
       clock: 33MHz                                                       
       capabilities: bus_master                                           
       configuration: driver=b43-pci-bridge latency=64 module=ssb         
  *-network:1                                                             
       description: Ethernet interface                                    
       product: RTL-8139/8139C/8139C+                                     
       vendor: Realtek Semiconductor Co., Ltd.                            
       physical id: 6                                                     
       bus info: pci@0000:06:06.0                                         
       logical name: eth0                                                 
       version: 10                                                        
       serial: 00:0f:b0:be:ea:6a                                          
       size: 10MB/s                                                       
       capacity: 100MB/s                                                  
       width: 32 bits                                                     
       clock: 33MHz                                                       
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s                                                           
  *-network:0                                                                                                                   
       description: Wireless interface                                                                                          
       physical id: 2                                                                                                           
       logical name: wlan0                                                                                                      
       serial: 00:14:a5:63:75:a6                                                                                                
       capabilities: ethernet physical wireless                                                                                 
       configuration: broadcast=yes ip=192.168.1.47 multicast=yes wireless=IEEE 802.11bg                                        
  *-network:1 DISABLED                                                                                                          
       description: Ethernet interface                                                                                          
       physical id: 3                                                                                                           
       logical name: pan0                                                                                                       
       serial: 82:3d:c7:80:65:43                                                                                                
       capabilities: ethernet physical                                                                                          
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes                         
```
sudo cat /etc/network/interfaces 
```                                                                              
# This file describes the network interfaces available on your system                                                           
# and how to activate them. For more information, see interfaces(5).                                                            

# The loopback network interface
auto lo                         
iface lo inet loopback          
address 127.0.0.1               
netmask 255.0.0.0               

# The primary network interface
auto eth0                      
iface eth0 inet dhcp           

auto wlan0
iface wlan0 inet static
address 192.168.1.47   
gateway 192.168.1.1    
dns-westell 192.168.1.1
netmask 255.255.255.0  
wpa-driver wext        
wpa-ssid Zapper        
wpa-ap-scan 1          
wpa-proto WPA          
wpa-pairwise TKIP      
wpa-group TKIP         
wpa-key-mgmt WPA-PSK   
wpa-psk <my psk>

```
 sudo ifdown -v wlan0
```
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/50firestarter
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
 route del default gw 192.168.1.1 metric 100 wlan0
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
```
 sudo ifup -v wlan0
```
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -q -f /var/log/wpa_supplicant.wlan0.log -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1

ifconfig wlan0 192.168.1.47 netmask 255.255.255.0               up
 route add default gw 192.168.1.1 metric 100 wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/50firestarter
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
```
uname -a
```
Linux dv8000 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

---

### Post by n1unqn on 2008-11-13
I just connected to a wired connection, ran the updates, rebooted, accepted the new broadcom driver, rebooted, and it's all working :)

Nice and easy.

---

### Post by feral555 on 2008-11-18
I just got my 4311 working on my Dell 1505 laptop.

If your wireless card doesn't seem to be working make sure you try the** Fn + F2** (on my laptop its the toggle wireless shortcut). 

After about a week of headaches installing and reinstalling both the wl and official drivers AND trying ndiswrapper with no success I did this on a whim and it worked (afer re-enabling the b43 driver via Hardware Drivers under System menu).

Hooray for wireless!!:)

---

### Post by yipperzz on 2008-11-18
hey everyone, a lot of info in this thread and if this has already been asked then i'm sorry.  hopefully someone can just answer this quick question.

my dell d600 with a bcm4306 wireless was working fine in 8.04.  i upgraded last night to 8.10 and everything was all messed up.  so i decided to just wipe it all and start clean on 8.10.  i can connect to unsecured networks fine, but i could not get it connected using wpa (tkip, aes, both) or wpa2 (tkip, aes, both).

on 8.04 i was using ndiswrapper, but with 8.10 it found the restricted driver so i went with that first.  since i was able to connect on an unsecured network, i'm assuming that the driver works.  but it's not working on wpa.  i'm also seeing a lot of other people having this issue (not just on broadcom cards) when going to 8.10.  

**for the people who are up and running on wpa, are you guys using the restricted drivers?  or are you using ndiswrapper?  thanks in advance. **

---

### Post by kannedheat on 2008-11-21
WPA just would not work for me, so I went with WEP encryption that setup went with no problems at all.  Unfortunately I have to change eight other system on my network.

---

### Post by Najubi on 2008-11-22
Hey

I just installed 8.10 on my computer and I am struggling with my Buffalo WLI2-PCI-G54-3 card. The problem is that on startup I get following message (from dmesg):
```
[    0.591541] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.591560] pci 0000:00:09.0: BAR 0: can't allocate resource

```
and 
```
[    0.628768] pci 0000:00:09.0: BAR 0: error updating (0x50010000 != 0x010000)

```

Also lspci gives me :
```
00:09.0 Network controller [0280]: Broadcom Corporation Device [14e4:0320] (rev 03) 
```

Does anyone have a clue why this happens and how to fix it?

EDIT: Problem solved. I changed it into different PCI-slot and now it works.

---

### Post by Ayuthia on 2008-11-22
> **Najubi said:**
> Hey

I just installed 8.10 on my computer and I am struggling with my Buffalo WLI2-PCI-G54-3 card. The problem is that on startup I get following message (from dmesg):
```
[    0.591541] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.591560] pci 0000:00:09.0: BAR 0: can't allocate resource

```
and 
```
[    0.628768] pci 0000:00:09.0: BAR 0: error updating (0x50010000 != 0x010000)

```

Also lspci gives me :
```
00:09.0 Network controller [0280]: Broadcom Corporation Device [14e4:0320] (rev 03) 
```

Does anyone have a clue why this happens and how to fix it?

From the searches for this error message, it does not look like this message is related to the wireless card.  The bugs that I am seeing seem to be more related to PCI devices.  Are you getting any more messages like that for other PCI devices?

Are you using the b43 driver from System->Administration->Hardware Drivers or ndiswrapper?  Can you go into the Terminal and post the results of:
```
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ndiswrapper
```
It will help us see what driver is being used and if the the card is responding to the driver.

---

### Post by coskierken on 2008-11-26
Ok, I managed to get the Broadcom 4306 Rev 2 wireless to work in this older HP laptop.  I read through many threads.  The main problem I still have is B43 module still wants to take control.  I have blacklisted it, but when it boots and you to a lshw -C network, the B43 is still there.  I don't know if it is picking it up from the firmware or not.  I installed ndisgtk and use the bcmwl5.inf Windows driver.  

What I did was:

sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

I know I repeated commands and when I check the modules, b44 is not there, but just to be safe, I -r it.  The only way to make sure it turned on was the duplicate ndiswrapper.  I just activate the file after boot.  What is the command to have it auto start at boot?  I would appreciate it.  Any other suggestions/help are welcome.  Thanks to all those helping in this thread.

---

### Post by kevdog on 2008-11-26
Just type this once:

```

echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; **modprobe ssb; modprobe b44;**' | sudo tee -a /etc/modprobe.d/ndiswrapper 

```

You can remove the statements in bold, if you do not want the ssb or b44 modules loaded after ndiswrapper -- Please note that the b44 module is for a wired broadcom device, and if you don't have a wired broadcom ethernet card -- you do not need this module.

And then I take it you have done the following to make sure that the ndiswrapper kernel module is loaded at boot?:

```

echo ndiswrapper | sudo tee -a /etc/modules

```

That should be it!!!  You could reboot if you want to check it out!!

---

### Post by frriction on 2008-11-27
no need of ndiswrapper look at this post i will solve ur problem [http://backports.ubuntuforums.com/showthread.php?t=959451](http://backports.ubuntuforums.com/showthread.php?t=959451)

I have dell inspiron with bcm4328 (rev03) card it works fine by following above post. just you need latest kernel, it works out of box.:lolflag:

---

### Post by msbealo on 2008-11-30
Hello,

Only in the last few days have I installed Ubuntu (8.10) for the first time. Everything looks good, but I'm having real difficulty with my Wireless card.

I've search and search for information and help on this issue and have finally decided to post this question.

OK. I have an Acer Aspire 1350 with a PCMCIA Belkin F5D7010. I've been trying to get this working with ndiswrapper using the bcmwl5a.inf driver.

The power light is on, I can see wireless networks but I can not connect.

Here are various outputs:

:~$ lspci -nn
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

I therefore installed the bcmwl5a,inf drivers.

:~$ ndiswrapper -l
bcmwl5a : driver installed
device (14E4:4320) present (alternate driver: ssb)

I'm using the driver from the R81433 package. This appears to be working.

:~$ lshw -C Network
*-network
description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 03
serial: 00:11:50:04:31:aa
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,06/25/2004, 3.40.7 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

p:~$ dmesg |grep -e Network -e wlan
[ 29.585133] wlan0: ethernet device 00:11:50:04:31:aa using NDIS driver: bcmwl5a, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[ 29.585720] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[ 118.170268] ADDRCONF(NETDEV_UP): wlan0: link is not ready


As I said above, I can see the available networks in the Network Manager (the icon my the clock) and if I do

:~$ iwlist wlan0 scan
wlan0 Scan completed :
Cell 03 - Address: 00:1CF:41:8E:3B
ESSID:"xxxxxxxxxxx"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:67/100 Signal level:-53 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK

Therefore at least something is working but I can't connect to the network.

:~$ ifconfig
wlan0 Link encap:Ethernet HWaddr 00:11:50:04:31:aa
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:5 Memory:34000000-34002000


My router is a Wireless Belkin Router which I can connect to with a wire. The security of the Belkin router is set for WPA/WPA2 and I can see the key so therefore know that I've got that bit right.

Could people please help me get the wireless card working. If you do reply to this could you please outline exactly what you mean as I'm not very good with Linux (despite having an on-off relationship for over ten years!)

I've also used the bcmwl5.inf driver and again, I can see the networks but can not connect to them.

Cheers,

Mark

PS. I did post this as a separate thread, but have not received much interest. Please help.

---

### Post by Ayuthia on 2008-11-30
> **msbealo said:**
> Hello,

Only in the last few days have I installed Ubuntu (8.10) for the first time. Everything looks good, but I'm having real difficulty with my Wireless card.

I've search and search for information and help on this issue and have finally decided to post this question.

OK. I have an Acer Aspire 1350 with a PCMCIA Belkin F5D7010. I've been trying to get this working with ndiswrapper using the bcmwl5a.inf driver.

The power light is on, I can see wireless networks but I can not connect.

Here are various outputs:

:~$ lspci -nn
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

I therefore installed the bcmwl5a,inf drivers.

:~$ ndiswrapper -l
bcmwl5a : driver installed
device (14E4:4320) present (alternate driver: ssb)

I'm using the driver from the R81433 package. This appears to be working.

:~$ lshw -C Network
*-network
description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 03
serial: 00:11:50:04:31:aa
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,06/25/2004, 3.40.7 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

p:~$ dmesg |grep -e Network -e wlan
[ 29.585133] wlan0: ethernet device 00:11:50:04:31:aa using NDIS driver: bcmwl5a, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[ 29.585720] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[ 118.170268] ADDRCONF(NETDEV_UP): wlan0: link is not ready


As I said above, I can see the available networks in the Network Manager (the icon my the clock) and if I do

:~$ iwlist wlan0 scan
wlan0 Scan completed :
Cell 03 - Address: 00:1CF:41:8E:3B
ESSID:"xxxxxxxxxxx"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:67/100 Signal level:-53 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK

Therefore at least something is working but I can't connect to the network.

:~$ ifconfig
wlan0 Link encap:Ethernet HWaddr 00:11:50:04:31:aa
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:5 Memory:34000000-34002000


My router is a Wireless Belkin Router which I can connect to with a wire. The security of the Belkin router is set for WPA/WPA2 and I can see the key so therefore know that I've got that bit right.

Could people please help me get the wireless card working. If you do reply to this could you please outline exactly what you mean as I'm not very good with Linux (despite having an on-off relationship for over ten years!)

I've also used the bcmwl5.inf driver and again, I can see the networks but can not connect to them.

Cheers,

Mark

PS. I did post this as a separate thread, but have not received much interest. Please help.

Can you also check:
```
sudo iwlist auth
```to see if the driver can work with WPA/WPA2?

---

### Post by msbealo on 2008-11-30
> **Ayuthia said:**
> Can you also check:
```
sudo iwlist auth
```to see if the driver can work with WPA/WPA2?


Ayuthia,

Thank you, please see the output below.

:~$ sudo iwlist auth
wlan0     Authentication capabilities :
		WPA
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		WPA2
          Current Key management :
		PSK
          Current Pairwise cipher :
		CCMP
          Current Pairwise cipher :
		TKIP
          Current Authentication algorithm :
		open

As far as I can see it all looks good, but I'm still unable to connect to the networks that I can see.

Mark

---

### Post by Ayuthia on 2008-11-30
You might try looking at the following links:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
and
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

They might help.  I am not too experienced in WPA/WPA2 though.

---

### Post by msbealo on 2008-11-30
> **Ayuthia said:**
> You might try looking at the following links:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
and
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

They might help.  I am not too experienced in WPA/WPA2 though.

Ayuthia,

I've already tried the second WPA thread with no success.. however I'd not come across the first one. I ran through it and Hey Presto! For a brief moment my card was talking to the router! This was with static and then dhcp. I then moved onto the encryption bit and turned my routers WPA/WPA2 back on and I lost everything and have since been unable to get the card talking again.. 

I think I'm slowly making progress. I think the drivers are working but something is still wrong. If only I could remember the precise steps I took to get the thing going.

Thanks for your help,

Mark

---

### Post by DaleFarrell on 2008-12-07
No one seems to have my problem. Ndiswrapper -l returns nothing.
Am using a 4306 rev 3 in an emachine. I only have the B43 showing in HardwareDrivers. How do get the STA drivers? Am using 8.10. Everything functions, but the wireless will not authenticate with or without WPA. To save my soul I could not even download a bcmwl5.inf driver. This is 3rd install, so I'm a little hesitant to fling a lot of dangerous commands at the kernel. Dale.

---

### Post by falcon61102 on 2008-12-07
When you type ndiswrapper -l into the terminal, what exactly happens?

Also, have you attempted to enable the drivers that are shown in the Hardware Drivers?

---

### Post by DaleFarrell on 2008-12-07
Absolutely nothing, except for returning to the next command line. I did activate the
b43, as prompted. FWCutter also activated itself. WPA Supplicant is installed. Tried
Wcuid on another install, but same result. I go into the authentication loop. Is this
important: my key is an uppercase name, when I return to the options for a key it has
changed into a string of numbers and letters. I have this same post near the beginning
of the forum. here is the demsg output:
 [   35.477930] input: b43-phy0 as /devices/virtual/input/input11
[   35.560091] firmware: requesting b43/ucode5.fw
[   35.654571] firmware: requesting b43/pcm5.fw
[   35.663698] firmware: requesting b43/b0g0initvals5.fw
[   35.698138] firmware: requesting b43/b0g0bsinitvals5.fw
[   35.824096] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   35.975645] Registered led device: b43-phy0::tx
[   35.976749] Registered led device: b43-phy0::rx
[   35.977410] Registered led device: b43-phy0::radio
[   36.191018] NET: Registered protocol family 17
[   36.796138] wlan0: authenticate with AP 00:14:6c:d7:2e:ce
[   36.996088] wlan0: authenticate with AP 00:14:6c:d7:2e:ce
[   37.196083] wlan0: authenticate with AP 00:14:6c:d7:2e:ce
[   37.396088] wlan0: authentication with AP 00:14:6c:d7:2e:ce timed out
I'm on an emachine laptop, and the wired works fine. ?????Dale

---

### Post by falcon61102 on 2008-12-08
Alright, since you are using b43Fwcutter, ndiswrapper is not going to work.  They are two different approaches to accomplish the same thing.  

Also, based on the dmesg, it doesn't look like the problem is with your drivers but rather with connecting to the network.  Would it be possible to drop the security temporarily on the network to test if you can connect through an unsecure connection so we can rule out driver/hardware issues and focus on the secure connection?

---

### Post by DaleFarrell on 2008-12-09
Say whaaat? The book I have says (implies) that the broadcom/windows drivers had to be
opened with Fwcutter, then Ndiswrapper could use them. I wonder why ubuntu automatically installed/activated Fwcutter. Do you think I should use the package manager to disable fwcutter? I set up another wifi router with no security enabled, and still have the no connection problem. Dale.

---

### Post by Ayuthia on 2008-12-09
> **DaleFarrell said:**
> Say whaaat? The book I have says (implies) that the broadcom/windows drivers had to be
opened with Fwcutter, then Ndiswrapper could use them. I wonder why ubuntu automatically installed/activated Fwcutter. Do you think I should use the package manager to disable fwcutter? I set up another wifi router with no security enabled, and still have the no connection problem. Dale.

The b43 driver needs some information from a proprietary firmware file so the b43-fwcutter application will cut the information needed from the specific piece of firmware.

As for NDISwrapper, it does not use b43-fwcutter.  It just uses the Windows wireless driver to make it work.

If you use the two at the same time, the two drivers will conflict each other.

---

### Post by DaleFarrell on 2008-12-10
Ayuthia, I apologize for you having to answer me twice. you are consistent, though, giving me the same advice each time! I am not sure which thread you monitor, so I'll repeat. If I remove fwcutter some driver should appear in the WindowsWirelessDriver space. I have read that Ndiswrapper gives higher network speeds. How bout I discontinue replies to the other thread, and stay here? thanks, Dale.

---

### Post by Ayuthia on 2008-12-10
> **DaleFarrell said:**
> Ayuthia, I apologize for you having to answer me twice. you are consistent, though, giving me the same advice each time! I am not sure which thread you monitor, so I'll repeat. If I remove fwcutter some driver should appear in the WindowsWirelessDriver space. I have read that Ndiswrapper gives higher network speeds. How bout I discontinue replies to the other thread, and stay here? thanks, Dale.

This thread would be fine.  Have you already loaded a Windows driver for NDISwrapper?  It should be a file like bcmwl5.inf  If not, you should try step 2g from this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It is the suggested driver for your card.

---

### Post by DaleFarrell on 2008-12-11
I did not load any drivers as the HardwareDrivers applet showed a b43 as activated. I can't tell from the dmesg output above if any driver is loaded. I  can see where it is asking for something, but to me it does not look like it gave an address for the device. I will install the driver from the Feisty link, but not til thursday eve. thanks, Dale in Seattle.

---

### Post by DaleFarrell on 2008-12-14
Progress? ndiswrapper -l now shows bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
I used package manager to disable b43fwcutter before I downloaded the driver, I wonder
if I need to use the fwcutter just once to extract the data,THEN disable it. At the moment I cannot access the mozilla servers to reinstall the cutter. As best as I can understand the results of the network commands it should work. Dale.

---

### Post by Ayuthia on 2008-12-14
> **DaleFarrell said:**
> Progress? ndiswrapper -l now shows bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
I used package manager to disable b43fwcutter before I downloaded the driver, I wonder
if I need to use the fwcutter just once to extract the data,THEN disable it. At the moment I cannot access the mozilla servers to reinstall the cutter. As best as I can understand the results of the network commands it should work. Dale.

It looks like you have a working driver for ndiswrapper.  You should be able to do the following and we can see if it works:
```
sudo modprobe b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If it does not show any wireless sites, you will need to check dmesg:
```
dmesg|grep ndiswrapper
```
It might provide some information on why it did not work.

You don't need to have b43-fwcutter.  It is used for the b43 driver only.  NDISwrapper does not use it and if b43-fwcutter is installed, it can cause conflicts with NDISwrapper.

---

### Post by DaleFarrell on 2008-12-14
Fwcutter is gone. WICD is now network manager. Ran your commands. rebooted. Nothing. I cannot access with or without security. I amm going back and forth to a Christmas tree, but the laptop is on. Dale.

---

### Post by dsiddens on 2008-12-20
No wireless with Intrepid 8.10 on an HP Pavilion AMD64, Broadcom 4311. 

Here's my lshw -C network:

  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:f5:bb:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 02:f2:06:8c:e3:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I'm very dumb about the control line, but I do follow directions!


Thank you, Doug

---

### Post by xjcannonx on 2008-12-20
Have you taken any steps to get your wireless working yet?

Try going to System-->Administration-->Hardware Devices

There should be a driver there you can select for your card

It appears you dont have a driver installed i.e. mine looks like this:
```
*-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:8d:40:70
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

Have you taken any steps to get your wireless working yet?

---

### Post by dsiddens on 2008-12-20
Here's the returns from two other comands:

lsmod|grep -e b4 -e ssb -e wl -e ieee80211
wl                   1085520  0 
ieee80211_crypt_tkip    18048  0 
ieee80211_crypt        14596  2 wl,ieee80211_crypt_tkip

modprobe --show-depends wl
insmod /lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211_crypt.ko 
insmod /lib/modules/2.6.27-9-generic/volatile/wl.ko

---

### Post by eternal_sage on 2008-12-20
ok guys. my wife's card was working great for the last 2 months... now its broken again. the only thing i can think of is the kernel update to 2.27.11 is what screwed it. i tried to refix it with everything that was in this tread, but to no avail. in fact, the script that got me working temporarily originally now broke my wi-fi AND wired internet. however, going back to the previous kernel fixed my issues for now. if you need all the info again, i'll post it up. thanks!

---

### Post by Ayuthia on 2008-12-20
> **eternal_sage said:**
> ok guys. my wife's card was working great for the last 2 months... now its broken again. the only thing i can think of is the kernel update to 2.27.11 is what screwed it. i tried to refix it with everything that was in this tread, but to no avail. in fact, the script that got me working temporarily originally now broke my wi-fi AND wired internet. however, going back to the previous kernel fixed my issues for now. if you need all the info again, i'll post it up. thanks!

You might try going back a kernel version to see if it works.  If it does, then it is most likely that it is the kernel that messed it up.  However if it does not, it could be network manager doing it.

---

### Post by Ayuthia on 2008-12-20
> **dsiddens said:**
> Here's the returns from two other comands:

lsmod|grep -e b4 -e ssb -e wl -e ieee80211
wl                   1085520  0 
ieee80211_crypt_tkip    18048  0 
ieee80211_crypt        14596  2 wl,ieee80211_crypt_tkip

modprobe --show-depends wl
insmod /lib/modules/2.6.27-9-generic/kernel/net/ieee80211/ieee80211_crypt.ko 
insmod /lib/modules/2.6.27-9-generic/volatile/wl.ko

Can you try checking dmesg to see if there are any issues:
```
dmesg|grep wl
```

---

### Post by AJB2K3 on 2008-12-20
my 4318 seems to be struggling on the acquiring ip address stage.
Could it be an issue between the huwie (modem router) and the 4318?

---

### Post by Ayuthia on 2008-12-20
> **AJB2K3 said:**
> my 4318 seems to be struggling on the acquiring ip address stage.
Could it be an issue between the huwie (modem router) and the 4318?

Are you using encryption?  If so, you might try turning it off and see if you can connect.  If it does connect, then you can try a different encryption option and see if you can connect.

---

### Post by DaleFarrell on 2008-12-20
I have tried everybody's suggestions. They kept me busy, but without success. I'm not
sure which command will give you the most help, so I'll shoot in the dark with the same
one dsiddens used:  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 01
       serial: 00:03:25:0b:f0:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.105 latency=64 module=ssb multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:77:55:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:20:68:8d:30:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
I'm going to plug in a usb wifi adapter for the heck of it. If the storm doesn't
knock out my power, I'll be here. Dale, in Seattle

---

### Post by Ayuthia on 2008-12-20
> **DaleFarrell said:**
> I have tried everybody's suggestions. They kept me busy, but without success. I'm not
sure which command will give you the most help, so I'll shoot in the dark with the same
one dsiddens used:  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 01
       serial: 00:03:25:0b:f0:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.105 latency=64 module=ssb multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:77:55:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:20:68:8d:30:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
I'm going to plug in a usb wifi adapter for the heck of it. If the storm doesn't
knock out my power, I'll be here. Dale, in Seattle

Can you do the following and post the results of the dmesg command at the end:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
dmesg|grep ndis
```
It looks like the ndiswrapper module did not start up for some reason.  Hopefully the dmesg command will provide some clues.

---

### Post by DaleFarrell on 2008-12-20
Here tis:
[   15.956072] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.531425] usbcore: registered new interface driver ndiswrapper
[ 4064.972308] usbcore: deregistering interface driver ndiswrapper
[ 4072.955034] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 4073.157965] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[ 4073.162771] ndiswrapper 0000:00:0c.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[ 4073.172590] ndiswrapper: using IRQ 10
[ 4073.570689] usbcore: registered new interface driver ndiswrapper

---

### Post by Ayuthia on 2008-12-20
> **DaleFarrell said:**
> Here tis:
[   15.956072] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.531425] usbcore: registered new interface driver ndiswrapper
[ 4064.972308] usbcore: deregistering interface driver ndiswrapper
[ 4072.955034] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 4073.157965] ndiswrapper: driver bcmwl5 (ASUS,03/22/2004, 3.60.7.0) loaded
[ 4073.162771] ndiswrapper 0000:00:0c.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[ 4073.172590] ndiswrapper: using IRQ 10
[ 4073.570689] usbcore: registered new interface driver ndiswrapper

And lshw -C network still shows that wlan0 is still disabled and using the b43 driver?  Are you able to scan for wireless sites:
```
sudo iwlist scan
```You only need to do this if it is not disabled.

---

### Post by DaleFarrell on 2008-12-20
I see all my neighbors and my own two. I have one on ch6 with no security, and one on ch11 with wpa. Here they are:          Cell 03 - Address: 00:0C:41:C2:5A:B3
                    ESSID:"monkeybiz2"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=76/100  Signal level:-53 dBm  Noise level=-68 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007a21505188
                    Extra: Last beacon: 292ms ago
          Cell 04 - Address: 00:0F:B3:88:3E:6D
                    ESSID:"pedoguado"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=68/100  Signal level:-61 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000090a01316122
                    Extra: Last beacon: 184ms ago
          Cell 05 - Address: 00:21:29:7E:1D:84
                    ESSID:"MONKEYBIZ"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=80/100  Signal level:-50 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000784ba1418a
                    Extra: Last beacon: 124ms ago
I get to the authentication phase and enlessly loop there. I reinstalled with the disc from Ubuntu, tho my image disc was summed ok. Dale.

---

### Post by Ayuthia on 2008-12-20
> **DaleFarrell said:**
> I see all my neighbors and my own two. I have one on ch6 with no security, and one on ch11 with wpa. Here they are:          Cell 03 - Address: 00:0C:41:C2:5A:B3
                    ESSID:"monkeybiz2"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=76/100  Signal level:-53 dBm  Noise level=-68 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007a21505188
                    Extra: Last beacon: 292ms ago
          Cell 04 - Address: 00:0F:B3:88:3E:6D
                    ESSID:"pedoguado"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=68/100  Signal level:-61 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000090a01316122
                    Extra: Last beacon: 184ms ago
          Cell 05 - Address: 00:21:29:7E:1D:84
                    ESSID:"MONKEYBIZ"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=80/100  Signal level:-50 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000784ba1418a
                    Extra: Last beacon: 124ms ago
I get to the authentication phase and enlessly loop there. I reinstalled with the disc from Ubuntu, tho my image disc was summed ok. Dale.

You can try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwconfig wlan0 essid monkeybiz2
sudo dhclient wlan0
```Let us know if it works or fails.

---

### Post by DaleFarrell on 2008-12-20
I can now connect to the ap without wpa,(monkeybiz2), but still no connection to 
the ap with encryption(monkeybiz) . Something happened tho! Dale
Uh Oh. I just rebooted, and now I cannot connect to the unsecured ap.
I re-entered your last script and I can now, again, connect to the non-wpa ap. Here is what your script produces:
 * Reconfiguring network interfaces...                                   [ OK ] 
dalejohnfiorillo@laptop:~$ sudo iwconfig wlan0 essid monkeybiz2
dalejohnfiorillo@laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7880
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:96:77:55:b2
Sending on   LPF/wlan0/00:90:96:77:55:b2
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 34092 seconds.
I tried editing the "essid monkeybiz2" to "monkeybiz". No connection, here is result:
   dalejohnfiorillo@laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
[sudo] password for dalejohnfiorillo: 
dalejohnfiorillo@laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
dalejohnfiorillo@laptop:~$ sudo modprobe ndiswrapper
dalejohnfiorillo@laptop:~$ sudo modprobe b44
dalejohnfiorillo@laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
dalejohnfiorillo@laptop:~$ sudo iwconfig wlan0 essid monkeybiz
dalejohnfiorillo@laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:96:77:55:b2
Sending on   LPF/wlan0/00:90:96:77:55:b2
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
receive_packet failed on wlan0: Network is down
Terminated
I'm getting thru the storm ok, but stuck here!Dale.

---

### Post by OceanWinds on 2008-12-20
I figure this falls under this thread.  My HP laptop uses broadcom wireless.  I am running 8.10 and it was running super slow online, and it has nothing to do with the connection.  Its all in ubuntu 8.10 because when I ran ubuntu 8.4 it ran super fast.

So I switched wireless drivers to try and get the internet work faster, and now when the computer starts up with ubuntu it locks up as soon as it searches for a network.  Good thing I have a Vista/Ubuntu dual boot system. 

Anyway... is there a fix for this... can I load ubuntu in such a way that it doesnt try to connect to the internet so I can load the old wireless driver back up.

P.S.  The only problems with ubuntu I have had so far has been with youtube (grey screen prob), bluetooth(bugs in GUI, and no wireless scanner support), and wireless connectivity(slow with one driver, and locks up with another).  Which is pretty good... but the trend in my experience with ubuntu are issues with wireless connectivity.

---

### Post by eternal_sage on 2008-12-21
> **Ayuthia said:**
> You might try going back a kernel version to see if it works.  If it does, then it is most likely that it is the kernel that messed it up.  However if it does not, it could be network manager doing it.

yea, as i said,t booting up in 2.27.10 worked... i just figured it may be something i could fix... if its just a kernel regression, then i'll just set her box to ignore that kernel in GRUB... thanks!

---

### Post by crotig on 2008-12-21
Hello. First time Ubuntu user here. I have an Acer Aspire 5310 using BCM4311 and a Belkin Wireless G router using WEP. 
The Ubuntu install went ok and I used a wired connection to update everything and after going through all the commands in this thread the wireless is seeing my neighbours WPA router but not mine. I turned off the encryption and it still cannot see my belkin. I plugged in the Belkin USB wireless stick to see what it could see and it shows the same, my neighbours network but not mine. My Asus Eeepc can see the router fine, as can my Samsung Omnia.

Here's the info :

lspci -nn```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
06:00.0 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0730]
06:00.1 SD Host controller [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller [1524:0750]
06:00.2 FLASH memory [0501]: ENE Technology Inc Memory Stick Card Reader Controller [1524:0720]
06:00.3 FLASH memory [0501]: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller [1524:0751]
```

lshw -c network
  ```
*-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:e3:e5:f8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.22 ip=192.168.2.4 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:9c:ab:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:56:2f:5f:62:a9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:6D:EF:36
                    ESSID:"linksys"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/100  Signal level:-82 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000010e22be1183
                    Extra: Last beacon: 8436ms ago

pan0      Interface doesn't support scanning.

```


I get the same Result using the STA Driver and the B43 driver.

Ideas Anyone?.

Thanks.

---

### Post by crotig on 2008-12-21
Bump:)

Anybody?.

---

### Post by anilp on 2009-01-02
Thanks to Ayuthia - it really helped me.
Unfortunately it is easier to connect to Wifi on Windows - no drivers to install :( and it took quite a bit of searching before I found this post. The Troubleshooting page for 8.10 did not consider the case where the device is on but the driver is disabled because it was not loaded at install. 
[https://help.ubuntu.com/8.10/internet/C/troubleshooting.html#troubleshooting-disabled](https://help.ubuntu.com/8.10/internet/C/troubleshooting.html#troubleshooting-disabled)

thanks,
Anil

---

### Post by lance bermudez on 2009-01-03
please look at my problem
[http://ubuntuforums.org/showthread.php?p=6488308#post6488308](http://ubuntuforums.org/showthread.php?p=6488308#post6488308)

---

### Post by lance bermudez on 2009-01-04
mine is working now so you could try to copy what i did and see if that works for you

---

### Post by EvilMonki on 2009-01-05
> **Ayuthia said:**
> If you copy that information and remove the sudo command, you can put them into /etc/rc.local:
```
gksu gedit/etc/rc.local
```
Add at the end of the file:
```
modprobe -r b43 b44 ssb wl
modprobe ieee80211_crypt_tkip
modprobe wl
modprobe b44
/etc/init.d/networking restart
```

awesome works in my BCM4311! Thanks:D

---

### Post by goathunter on 2009-01-05
Would someone please be able to have a nosey at my problem as well?

[http://ubuntuforums.org/showthread.php?p=6379588#post6379588](http://ubuntuforums.org/showthread.php?p=6379588#post6379588)

cheers

I had got wireless working and then it just stopped for no reason. Was able to reconnect initially a few times by rebooting but then it just stopped connecting altogether. Any help would be appreciated.

---

### Post by primski on 2009-01-06
What about the restricted 'WL' driver for broadcom's wireless cards?

Prior to 2.6.27-11 kernel update the thing was working perfectly, way better than ndiswrapper - had it on Hardy, but since the 2.6.27-11 kernel update - i no longer get this driver under 'Restricted drivers manager' therefore nonfunctional wireless card.

I know, i know it's in the proposed updates - i have them enabled - and am running 2.6.27-10 kernel for now until this is resolved. I cannot find any bug tickets about this problem, is it just me ? Is it even worth bugging over it while it's in the proposed repo?

---

### Post by Ei8htArcher on 2009-01-06
I am having a problem with my wi-fi. I am connecting to the network and have access, but the notification icon in the tray shows that the computer is not connected. I'm using a BCM4312 with the restricted STA driver. It seems to work fine, except for the schizoid notification. Any help on how to correct that?

---

### Post by Ayuthia on 2009-01-06
> **Ei8htArcher said:**
> I am having a problem with my wi-fi. I am connecting to the network and have access, but the notification icon in the tray shows that the computer is not connected. I'm using a BCM4312 with the restricted STA driver. It seems to work fine, except for the schizoid notification. Any help on how to correct that?

Not for sure which schizoid notification you are referring to, but one of them is some kind of network connection monitor.  If you left-click on it, a screen should pop up showing which connection it is monitoring.  Make sure that it matches with your connection.

---

### Post by Citizen_Kane01 on 2009-01-07
Thanks so much! Work a treat eve for a complete newbie.

---

### Post by Paul S on 2009-01-10
Something's wrong with jockey on 8.10 here.  It offers the STA driver, but won't activate it.  I had to use your script in post 69 to create a /etc/modprobe.d/wl file and reboot.  But, that is working, and so far, it has come up after suspend / resume cycles.  I did have to add /etc/pm/config.d/00wl_module with
SUSPEND_MODULES="ieee80211_crypt ieee80211_crypt_tkip wl", otherwise, it would not resume.

paul :~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

The wl module was working on hardy.

---

### Post by Paul S on 2009-01-10
BTW, I think you need to use double quotes to get the backticks to get the date printed in your script in post 69 [http://ubuntuforums.org/showpost.php?p=6077712&postcount=69](http://ubuntuforums.org/showpost.php?p=6077712&postcount=69)

This works here:

echo -e "#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe ieee80211_crypt_tkip; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;" | sudo tee -a /etc/modprobe.d/wl

---

### Post by Ayuthia on 2009-01-10
> **Paul S said:**
> BTW, I think you need to use double quotes to get the backticks to get the date printed in your script in post 69 [http://ubuntuforums.org/showpost.php?p=6077712&postcount=69](http://ubuntuforums.org/showpost.php?p=6077712&postcount=69)

This works here:

echo -e "#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe ieee80211_crypt_tkip; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;" | sudo tee -a /etc/modprobe.d/wl

Actually, your option or the one in post 69 should work.  The script was modified from the ndiswrapper no-fluff site:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3)
It also uses the single quote.  

Regardless, I am glad to see that you were able to get it to work.

---

### Post by thewOndErEr57 on 2009-01-16
UPDATE for the Belkin F5D7050 USB wireless dongle.

There's an up coming kernel release currently in Intrepid proposed that solves the issue by natively supported this device with rtl8187.

I have written a full tutorial on how to get it set up.

Read the tutorial here:
[Belkin F5D7050 - working natively on Ubuntu - SOLVED]("http://linuxsoftwareblog.com/blog/?p=30")

Leave comments on the blog if you find this useful for you!

---

### Post by kevdog on 2009-01-16
> **thewOndErEr57 said:**
> UPDATE for the Belkin F5D7050 USB wireless dongle.

There's an up coming kernel release currently in Intrepid proposed that solves the issue by natively supported this device with rtl8187.

I have written a full tutorial on how to get it set up.

Read the tutorial here:
[Belkin F5D7050 - working natively on Ubuntu - SOLVED]("http://linuxsoftwareblog.com/blog/?p=30")

Leave comments on the blog if you find this useful for you!

Link is broken

---

### Post by pencilpusher on 2009-02-07
I hope someone can help me out. I've installed 8.10 on my Dell and the driver installed fine (see below). It connects to my school wireless networks but it will not connect to my home router. It doesn't even see it. The router is a D-Link dl-524. It has encryption turned off. Vista is installed on this computer and it connects with no problem.  
What do I need to do?


  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:06:8c:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by ganzeegeezer on 2009-02-07
> **Ayuthia said:**
> For those of you who don't have a working connection in Ubuntu and cannot use the wl driver, here are some instructions on what to download so that you can install it in Ubuntu:

This will only work in Intrepid (and not the older versions of Ubuntu).  This is a revised version of this [thread]("http://ubuntuforums.org/showthread.php?t=779754")(changed because the firmware is different in Intrepid):

[B]Option 2
For those without a working internet connection[/B]

**If you have a Intrepid install CD, **
Insert your CD and do the following:
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter
```
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**
Now skip down to the Downloading Firmware section.

**If you don't have a Intrepid install CD**
You will have to find a place with a working internet connection.  Go to this link:
[http://packages.ubuntu.com/intrepid/utils/b43-fwcutter](http://packages.ubuntu.com/intrepid/utils/b43-fwcutter)
Download the version that you need--amd64 for 64-bit and i386 for 32-bit.  Copy the file to your home directory and do the following:
64-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_amd64.deb
```
It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

32-bit:
```
cd
sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
```
It is possible that the _011-4ubuntu1_ portion is another number.
**Make sure that you say no or cancel when the installer asks you to find/download the firmware for you.  It will get stuck because it is thinking that there is an internet connection.**

**Downloading Firmware**
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```
Copy those files to your home directory.  In the Terminal/Konsole/xterm window do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

Thanks, works a treat :)

---

### Post by lms5yc13 on 2009-02-08
Ok so like everyone else, my bcm 4318 driver doesn't work correctly. I can access the networks that are around me and connect successfully. But my problem is staying connected. The connection will only last for a few minutes then kicks me off. After that, I can't reconnect for some reason. I enabled the driver that Ubuntu suggests, but it won't work consistently. Any suggestions on what I should do?

---

### Post by alphatrose on 2009-02-19
> ** said:**
> Sorry.  Can you try the following:
```
sudo modprobe -r b43 ssb bcm43xx wl
sudo depmod -a
sudo modprobe wl
sudo /etc/init.d/networking restart
```

Hopefully that will get it started.  
Thanks for this. Been trying ndiswrapper + dl'ing Linux driver from broadcom without success after installing intrepid on my daughter's vista laptop. I'd been banging on about ubuntu for months 'til she agreed then ARRGggh no wi-fi. entered these 4 short lines + I'm now No1 dad (for @least 5more mins lol) Thanks again Ayuthia:D

---

### Post by 2scott on 2009-02-20
Hi - I had GREAT SUCCESS getting the same wireless card working using this link from the documentation section - also I posted some minor corrections to the instructions yesterday in a new thread.  This should solve your problem.  [http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/](http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/) (Tested and Proven to work, Source code is fully viewable).  Look forward to your results!

---

### Post by yarilo123 on 2009-03-24
Hi,

I followed your instructions but that didn't solve my problem... I don't know why, but since I updated my Ubuntu to interpid and installed the necessary "drivers" for the WLAN and worked for about one week, and after that, for no specific reason it just stoped working... When I run 
```
sudo iwlist scan
``` it gives the following result:
```
wlan0     Interface doesn't support scanning : Network is down
```
for ```
iwconfig
``` I get:
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I'm relatively new to Ubuntu so I'll need some help finding the solution. Tnx in advance :)

---

### Post by Ayuthia on 2009-03-24
> **yarilo123 said:**
> Hi,

I followed your instructions but that didn't solve my problem... I don't know why, but since I updated my Ubuntu to interpid and installed the necessary "drivers" for the WLAN and worked for about one week, and after that, for no specific reason it just stoped working... When I run 
```
sudo iwlist scan
``` it gives the following result:
```
wlan0     Interface doesn't support scanning : Network is down
```
for ```
iwconfig
``` I get:
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I'm relatively new to Ubuntu so I'll need some help finding the solution. Tnx in advance :)

Welcome!  Can you please go into the Terminal and post the results of:
```
lshw -C network
```
This will let us see if the firmware has been installed and it is using the correct wireless module.

It also looks like your network is not up yet.  You might try:
```
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will try to bring up your wireless and then scan for sites.

---

### Post by jng085 on 2009-03-31
Hello I am new to ubuntu and i have been trying many steps in this thread however i am not able to get wireless up. i did a fresh install and tried to go the ndiswrapper route with no success. Here is my info below

```
james@Fios:~$ sudo iwlist scan
[sudo] password for james: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

james@Fios:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

james@Fios:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:18:36:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.4-1 ip=192.168.1.6 latency=0 module=e1000e multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:69:09:1d:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 8e:70:74:d2:8b:df
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
james@Fios:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
```

---

### Post by digitalramble on 2009-04-06
I appear to have the dreaded 4315, but I thought I'd add more info to the mix.

First of all:
 lspci -vnn | grep 14e4
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

Now then, here's my experience.  This is a brand new HP laptop, so I went ahead and installed the latest version of 9.04 a few days ago.  The wireless worked out of the box for a few hours (on a mac address based wireless connection).  When I shut it down and went home to my WEP based wireless, it went into an infinite loop of asking me for the (verified correct) WEP password, getting it, then coming back for the WEP password lather rinse repeat.  After rebooting, the wireless icon (network manager) behaved as if there simply was no wireless network to be had.

I thought perhaps 9.04 wasn't quite prime time for this, installed 8.10 and the wireless never worked, just sat there and pretended that no wireless (mac address or WEP or whatever) even existed.  

But all the lspci and iwconfig and ifconfig checks looked like it knew the hardware was there.

So for the heck of it I reinstalled 9.04, and I had the same thing happen, only it connected just fine to the WEP wireless for several hours before something happened and it dropped back into the cycle of asking me for the WEP password over adn over again until reboot after which it couldn't see any existing wireless at all.

Dropped in a USB wireless dongle and was connected in 10 seconds.  

I have not done anything else besides this, I was researching the b43/legacy stuff until I found out that 4315 is unsupported (as described in this undated site: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) ) and eventually stumbled on this page after more googling.  The only advice i found on this thread was to try the ndiswrapper (which I have not) or the Broadcom STA driver.  Is the latter the proprietary driver that gets listed under System->Administration->Hardware Drivers?  Because if so, that was installed and activated from the get go on the 9.04 installation (but not on the 8.10)...

Comments, etc, greatly appreciated.  This is somewhat annoying, because when I got this laptop I was under the impression they had Intel wireless installed in this model (dv4tse), *grumble*... I did not want to get tangled in broadcom...

---

### Post by Favux on 2009-04-07
Hi digitalramble,

When NM asks for the password is the password box filled with what looks like a hex hash?  If so this work-around may apply to you:

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

Might be worth a look.

---

### Post by digitalramble on 2009-04-12
> **Favux said:**
> Hi digitalramble,

When NM asks for the password is the password box filled with what looks like a hex hash?  If so this work-around may apply to you:

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

Might be worth a look.

Thanks for the pointer...I checked it out, but it appears to discuss issues with trying tu use WPA -- I am actually using plain ol' WEP (don't want to futz with a working router, esp as I'm not the only one using it :D )

However, after thinking about what that article had to say about how NM seems to rewrite the config files (badly), and after discovering that it was a fresh reinstall of *NM* that solved its inability to see/use the wireless, I set it to not auto connect as kind of a test...it's been working for a couple days now, so I have my fingers cross...thanks!

---

### Post by Favux on 2009-04-12
Hi digitalramble,

Good deal, I hope it keeps working for you.  And I should have said last time that yes the Broadcom STA wireless driver (wl) is the proprietary Broadcom driver.

---

### Post by blackzmage on 2009-06-02
I get the "cannot open input file" when I enter "sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_m"

---

### Post by Ayuthia on 2009-06-02
> **blackzmage said:**
> I get the "cannot open input file" when I enter "sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_m"

You might to make sure that you are in the correct directory.  Also, it looks like you did not get the full name of the file.  Did you mean to use:
```
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
```

---

