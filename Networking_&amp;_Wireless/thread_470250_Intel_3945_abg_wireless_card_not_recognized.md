---
title: "Intel 3945 abg wireless card not recognized"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by ocrickard on 2007-06-10
Hello, I'm a relatively new user of Ubuntu, so please pardon my inexperience with this issue.  I recently installed Ubuntu 7.04 on my Gateway NX860XL laptop.  Everything seems to work fairly well except for the wireless card.  The computer has an Intel 3945 abg card, and it seems as if the system does not recognize it at all.  I tried unsuccessfully to install the ipw3945 drivers from the sourceforge project, but I can't seem to get it to work.  The ipw3945 daemon won't start, giving this message:
2007-06-10 17:11:48: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
I can load the ieee80211 module, but not the ipw3945 module, because it gives me the same message as the daemon:
ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
The output of lspci is below:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```
and iwconfig as well:
```
lo        no wireless extensions.
eth0      no wireless extensions.

```
I had seen on a blog that someone's Restricted Drivers Manager provided a driver for this card, but mine does not.
I don't know where to go next with this problem.  Any help would be immensely appreciated.  I apologize if this has already been solved elsewhere in this forum, I believe that I searched quite thoroughly.
Thanks in advance,
Oliver Rickard

---

### Post by Jamshedk on 2007-06-10
Did the wireless card dissapear after you installed NVIDIA drivers?

---

### Post by ivesjd on 2007-06-10
```
sudo update-pciids
```
then ```
 lspci 
``` 
should output the wireless chipset, see where it is saying its unknown? Post that output, should help people help you :)

---

### Post by kitpierce on 2007-06-11
I am having the same problem with a Dell Inspiron 6400.  When I followed the pciids command I get the following output from lspci:

[HTML]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
[/HTML]

Just so you know, I followed the how to from this link, but it didn't recognize my wireless care (I think the instructions are written for a different wireless card than mine.)  Please let me know what I need to do to reverse any damage I may have done by using the above as well as how to install the PRO/Wireless card.

Any help would be most appreciated.  Thanks!

---

### Post by chili555 on 2007-06-12
kitpierce-
Your card *is* recognized:> 0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)It is *not* a 3945, it's the newer 4965. Please search this forum for '4965' and you will see instructions to install the Windows driver with ndiswrapper.

---

### Post by kitpierce on 2007-06-12
Wow, thanks Chili555!  I can't believe I missed that really important detail (uber-noob here...)  I must have been working on this too late at night.  Thanks for the heads up; I have posted a request in the appropriate thread ([here.]("http://ubuntuforums.org/showthread.php?p=2829341#post2829341"))  Thanks again!

---

### Post by ocrickard on 2007-06-12
Thank you, Ivesjd for your suggestion.  I got tired of trying to get it to work, and installed fedora before revisiting this forum.  Sadly, Fedora 7 also does not recognize it, so I'm going to install Mint 3.0 in a few minutes and see what I can do with that.  I'll post the output of your suggestion if it doesn't work.
In response to Jamshedk - No, the wireless card was never recognized.  I don't think that the Nvidia drivers affected it, but I'm not that sure.
Thank you for your assistance,
Oliver Rickard

---

### Post by iammeagain on 2007-07-01
I am having the same problem, I have got a Gateway nx860xl also and it doesnt recognize the wireless card. my output for lspci is almost the exact same as the first posted. If anyone finds a way to enable it please post, because Vista sucks and I hate using it](*,) , but I need to be able to use wireless internet. 

I don't want to mess with too much, because this laptop is my new toy and I don't want to spend hours fixing it. so far i have found this:

> Using the network manager that comes with Feisty (network-manager-gnome) Didn't try WEP, but it does work with WPA and WPA2

:EDIT:

Actually I don't think I tried it with WPA2, I upgraded my laptop before I changed to WPA2.

So the intell 2915abg works with WPA (didn't test WPA2)

[COLOR="Red"]Now I have the intel 3945 and it works with WPA2 (didn't try WPA)[/COLOR]

I use the standard Network manager for both.
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=488801&highlight=3945+intel](http://ubuntuforums.org/showthread.php?t=488801&highlight=3945+intel)[/COLOR]

---

