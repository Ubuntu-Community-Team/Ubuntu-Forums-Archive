---
title: "Gateway wireless help!!"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by wildseven on 2008-03-08
hello! i have a gateway MT6705 with Gutsy on it. I'm having a hard time getting the wireless to work. I'm pretty confused as to what is happening. It can see wireless network around me. I can see wlan0 in my iwconfig and ifconfig...but it won't connect to them. I won't get an IP. 

i tried it manually.
```

sudo ifconfig wlan0 down
sudo dhclient -r
sudo iwconfig essid "essid"
sudo iwconfig mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0

```
but nothing..looking at the iwconfig wlan0 i can see it is associated with my essid....but when i try to get an IP via dhcp.I get nothing I will just send DHCP broadcast packets and not get anything..then the dhcp service goes to sleep.



Any idea? Ethernet work


Here is my lspci if that helps.
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```



Any help would be great thanks!

---

### Post by alphacrux on 2008-03-26
Hi wildseven! Let me see if I can help you...

First, are you using an unsecured network? If not are you using WEP or WPA? 

Second, do you know what driver you're using, or the name of your network card?  Finding these out will likely help point you in the right direction, then we'll have a likely set of problems.
I don't see your wireless device from lspci, or at least its not obvious. Post the results of "lshw -C network". You may have to get lshw from aptitude.
Also "lsmod" will display all the modules your running. We'll want this to see what wireless driver your using, if any.

Lastly, can I see the results of iwconfig after you associate your essid? Also the results of dhclient wlan0? Check "dmesg" after each of these and look for any errors.

Hopefully one of these will give us the answer :)

---

