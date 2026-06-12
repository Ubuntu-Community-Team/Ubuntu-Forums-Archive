---
title: "Broadcom Gusty"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by ep3w on 2007-10-20
I have a dell 1390 wlan card with a broadcom chipset.  I enable the restricted drivers and I get my wireless network to show up, but I can never connect to it.  I know the RM firmware is limited to 12mb, but I figured i should see if I can get it to work with that first.  Should I try something else first?  It worked great in feisty using the install script found on this forum.  Any thing I  can do to get this to work?  Thanks for any help!

Here is my lspci output
```
 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
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
01:00.0 VGA compatible controller: nVidia Corporation G72GL [Quadro FX 350M] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```

---

### Post by brianbarry on 2007-10-20
I had to install and configure wifi-radar to get my Broadcom card to work.  wifi-radar provides addition settings that seem to be needed.  Hope this helps you.

Brian

---

### Post by Cha1ns on 2007-10-20
I have the same problem and the same wirless card, It worked fine in fiesty once I installed ndiswrapper (Which I had to compile from source to make it happen because the one in the repository wasn't new enough). But now with Gutsy, it did not work apon first install (with wifi-radar) but it offers to install the restricted firmware, so I did that.  That makes both green lights turn on the card light up, but does not show any wireless networks even with wifi-radar It is probably because I upgraded from 7.04 to 7.10. My system already has ndiswrapper on it and says it still has the driver for the wireless card installed.

I've attempted various things including disabling ndiswrapper module, then removing the firmware and renabling ndiswrapper. Along with many many reboots. An interesting problem is that ifconfig shows an ETH1 instead of wlan0, but wifconfig shows that eth0 has wireless extensions.

---

### Post by robostang 548 on 2007-10-20
I have a similar problem.  My upgrade failed so I did a fresh install of gutsy.  I had my wireless working with ndiswrapper on 7.04.  When I got done installing gutsy I installed my restricted drivers and the blue light on my wireless card came on (meaning it was up and running).  When I us iwconfig my wireless comes up as eth1.  When I click on my network applet it shows no wireless networks so I click on "connect to other wireless network" and then the applet crashes.  I tried ndiswrapping using the same tutorial I used to get my wireless working on 7.04 but still no luck.

---

### Post by robostang 548 on 2007-10-20
I just got the problem I had posted previously fixed.  I went into restricted drivers and removed the broadcom firmware.  Then I said "sudo modprobe -r bcm43xx" then I just followed all the procedures for ndiswrapping my driver.  After I installed the driver with ndiswrapper I used the following code:

```
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

```

Then I restarted my computer and it worked.  I'm glad I got my wireless up and I hope this will help whomever is having the same problem.  I am a bit disappointed though.  I got really excited when I found out gutsy would work with broadcom without ndiswraping.

-Don

---

### Post by jardo on 2007-10-21
friends i have your similar problems...at the end installed ndiswrapper....with restricted drivers seem working....see the wireless network,but it gives problems when u try to connect to it

---

