---
title: "Newbie"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by xxstitches24xx on 2009-02-21
Ok i am completely new to all this computer talk mumbo jumbo. I have an Acer 3680 laptop with an Atheros wlan card. I can connect to the internet using the wire but still cant figure out the programming for wireless. Can anyone give me an idiot proof solution??

---

### Post by vikramaditya on 2009-02-21
first!

EDIT - sorry, just had to beat the hotshots around here!  You might want to look into wicd as your wireless "solution" - just be sure to completely read its documentation!

---

### Post by xxstitches24xx on 2009-02-22
Ok so i downloaded wicd. in the second step i put a command in a terminal and now its asking me for a sudo password.  But it wont let me type at all.  Can you help?

---

### Post by Mazza558 on 2009-02-22
When you type your password with Sudo, it doesn't show up - this is for security reasons. Just type as if you could see it and press enter.

---

### Post by xxstitches24xx on 2009-02-22
Tried that that but it keeps ssaying "Sorry try again"

---

### Post by xxstitches24xx on 2009-02-22
Of course i say that and then it accepts it,
 lol.

---

### Post by Doug11 on 2009-02-22
The easiest way I found with my Acer was to go to System>Administration>Hardware Drivers and enable the Broadcom B43 driver. You will need to be hooked into your wired connection to do so. After that, all I had to do was setup my info in Network manager. This is just one of the many ways to go about it.

---

### Post by xxstitches24xx on 2009-02-22
When i go into Hardware Drivers it only lists my Atheros card.
And i need help configuring my system.

---

### Post by ja660k on 2009-02-22
hey.
i had this same problem, i have atheros wireless too
first a few questions.

can you login to windows? ie dual boot?

also can you run this in terminal and give the output
```
lspci
```
and
```
iwconfig
```


this is alot easier then people make it out to be

---

### Post by xxstitches24xx on 2009-02-22
No i dont have windows on this computer but do have access to windows xp

raymond@raymond-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

raymond@raymond-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by ja660k on 2009-02-22
okay well that makes things a little bit harder. That wont help because we need this computers wireless driver.

from this
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

we can tell what driver you need.
AR242x or AR5007EG

but first you need to disable ubuntu to manage the hardware
because we will using ndiswrapper.
go to system>Administration>Hardware Drivers
and there should be 1 or 2 things to do with your wireless.. make sure they are UNCHECKED

```

sudo apt-get install ndiswrapper
sudo apt-get install ndisgtk

```

as soon as we find a proper driver we can patch it and bobs your uncle

but for now i cant find driver so bare with me for a few minutes ...

Okay, i found this
[http://www.opendrivers.com/freedownload/237047/ralink-rt61-rt2500-wireless-pci-driver-1.2.0.0-whql-windows-9x-2000-xp-xp-x64-download.html](http://www.opendrivers.com/freedownload/237047/ralink-rt61-rt2500-wireless-pci-driver-1.2.0.0-whql-windows-9x-2000-xp-xp-x64-download.html)

im not sure if it will work, but one way to find out...

DL the file unzip it then navigate to Drivers/XP-x32/
and you want net5211.inf

then in terminal run 
sudo ndisgtk

then install new driver and select the .inf

then reboot and HOPEFULLY it will work

goodluck

---

