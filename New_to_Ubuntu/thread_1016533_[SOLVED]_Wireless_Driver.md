---
title: "[SOLVED] Wireless Driver"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by SportsGuy2 on 2008-12-20
I just installed ubuntu, and I absolutely love it!!

Everything is running smooth, but I just can't get my wireless internet to work... :(

Can somebody help me with this?

---

### Post by nhasian on 2008-12-20
first lets find out what network adaptor you have with

```
lshw -C network
```

---

### Post by SportsGuy2 on 2008-12-20
*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ed:f2:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=************ latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:60:12:c6:6e:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:16:ce:07:de:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by wolfen69 on 2008-12-20
when you click the network icon on the taskbar, does it show available networks?
also, go to system>administration>hardware drivers and see if your wireless driver is there.

---

### Post by SportsGuy2 on 2008-12-20
> **wolfen69 said:**
> when you click the network icon on the taskbar, does it show available networks?
also, go to system>administration>hardware drivers and see if your wireless driver is there.

I don't see it there... I only see the b43 thing.

---

### Post by xjcannonx on 2008-12-20
I believe all you need to do is to activate that driver

---

### Post by SportsGuy2 on 2008-12-20
i can't get it to activate... i click on activate but the "button" stays gray, and not green

---

### Post by linuxford on 2008-12-20
I think I got the same exact wireless card as you. Here is my output:

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:18:09:7f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:ce:f4:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.3 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:26:b0:79:ec:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Here is what I used to fix it, by the way, I have to broadcast my SSID otherwise it doesn't work, or it will for some time, and then not work, so I left my broadcast ssid ON all the time:
----------------------------------------------------------------------
NOTE: THIS TUTORIAL WAS MADE USING LINUX UBUNTU 2.6.24 KERNEL. IT HASN’T BEEN TESTED ON OTHER DISTROS NEITHER OTHER KERNELS. DO IT AT YOUR OWN RISK.

Steps:

   1. Open the terminal
   2. type this
     ```
 sudo apt-get install build-essential
```
   3. copy and paste OR type this (each is a separate line in the terminal)
      ```
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
      tar xjf b43-fwcutter-011.tar.bz2
      cd b43-fwcutter-011
      make
      cd ..
```
   4. then
      ```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
      wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
      tar xjf broadcom-wl-4.80.53.0.tar.bz2
      cd broadcom-wl-4.80.53.0/kmod
      sudo ../../b43-fwcutter-011/b43-fwcutter -w "/lib/firmware" wl_apsta.o
```
   5. Now reboot Ubuntu and you should be good to go.

Note that you FIRMWARE_INSTALL_DIR might change with the distro.
------------------------------------
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219775)

---

### Post by igknighted on 2008-12-20
The above post simply tells you what ubuntu will do automatically when you click to activate that driver.  However, it appears you are not connected to the internet.  You need to be online for it to work.  The driver is installed with ubuntu, but there is a piece of firmware that must be installed as well for your card to be functional.  Due to license restrictions, this cannot be shipped on the CD.  You can do it the automatic way once online, or download the firmware file from another computer and bring it over via usb stick (or any other way), and follow these directions (a modified version of the above poster's, skipping some needless complication and accounting for the fact that you are not online).

1) Get the firmware.  Here is the link to the file, put this into your browser and it should download.  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

2) Place the firmware in you home folder (/home/<your_username>)

3) Open a new terminal and run these commands:
```
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o
```

3a) If the last command returns a message saying that the command b43-fwcutter is not installed, then go to packages.ubuntu.com, search for b43-fwcutter on the bottom and download the .deb file for your architecture (probably i386).  Simply double clicking this file on your ubuntu system should install it.

4) Reboot, and it should now work

---

### Post by SportsGuy2 on 2008-12-20
I don't know if I'm doing it wrong or something, but I still can't get it to work...

---

### Post by anewguy on 2008-12-20
If you could, please post line for line (screen images would be even better!) of exactly what you are doing (you know the old saying - not what you THINK you are doing, but verbatim as you do it).  This may help us.

there is another option for that particular wireless - using ndiswrapper.  Start up synaptic package manager and look for ndiswrapper and utilites - if they already have a green box then they are installed.  If they are not installed, and you can't at least temporarily hard wire your PC to the router/modem, then post back and I'll give you the simple instructions for getting these off of the LiveCD.

Dave :)

---

### Post by SportsGuy2 on 2008-12-20
would it make a difference if i am booting ubuntu off of my flash drive from unetbootin? so is it still the live cd version?

---

### Post by anewguy on 2008-12-20
I've never done that, so I don't know.  Try running synaptic anyway to see if ndiswrapper and utils is installed.  Also, again I've never done it so I don't know, but the reason the driver isn't able to be enabled may be that you used the USB stick - perhaps it doesn't allow that type of change.

dave :)

---

### Post by SportsGuy2 on 2008-12-20
and everytime i reboot, everything is reset, like my mozilla preferences, and my wallpaper, so i don't know if anything i am doing is any good when i reboot.

---

### Post by anewguy on 2008-12-21
I'm going to make an assumption here - when you load ubuntu from your flash drive, you are actually just loading in the LiveCD stuff, so no change would ever be permanent, no driver loading will ever work, etc..  If you have the room, I would recommend shrinking the size of your Windows partition and going with a dual-boot.

Dave

---

### Post by SportsGuy2 on 2008-12-21
I would do that, but I would like to have it on my flash drive so I can take it with me, at home and work

---

### Post by nhasian on 2008-12-21
its not going to work off a liveCD but if you have a persistant boot with a liveCD then you can add updates to it.  Use the ethernet (wired) to access the internet to download all the latest updates for Ubuntu 8.10.  Then after you reboot you should be able to go to System -> Administration -> Hardware Drivers and enable the one for your broadcom wireless adaptor.

---

