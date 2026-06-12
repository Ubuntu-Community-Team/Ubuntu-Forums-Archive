---
title: "Medion Akoya E1312 - No Wireless"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Glyn Hughes on 2010-02-05
I've got a Medion Akoya E1312 laptop  - I had to fiddle a bit to get the wireless working - I obtained an RTL8101E driver for Windws2000 and installed it using the 'Windows Wireless Drivers' software.

The Wireless icon now appears, it finds and displays local networks, properly asks for passwords but steadfastly refuses to connect. I have checked that the wireless is switched on (there is a little lamp on the keyboard) and that I've got the right password.

Have I got the right driver? Any ideas?

---

### Post by ikt on 2010-02-05
If no other responses I'd give :

[https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide)

A run through, I link to it a lot because I find it very comprehensive.

---

### Post by bkratz on 2010-02-05
> **Glyn Hughes said:**
> I've got a Medion Akoya E1312 laptop  - I had to fiddle a bit to get the wireless working - I obtained an RTL8101E driver for Windws2000 and installed it using the 'Windows Wireless Drivers' software.

The Wireless icon now appears, it finds and displays local networks, properly asks for passwords but steadfastly refuses to connect. I have checked that the wireless is switched on (there is a little lamp on the keyboard) and that I've got the right password.

Have I got the right driver? Any ideas?

Well, I don't think you do.  The device RTL8101E is the ethernet device not the wireless one, I think.
See this thread
[http://ubuntuforums.org/showthread.php?t=820026](http://ubuntuforums.org/showthread.php?t=820026)

you might type in lspci in the terminal and look for the network controller and see if it says something like 802.11 and the device name and repost it here.

---

### Post by Glyn Hughes on 2010-02-05
Thank you for that suggestion, unfortunately the Wireless troubleshooting guide at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) fails me at "If you can see an entry under the Wireless Connections tab, then you have a working connection already and simply need to activate it. Select the entry and click on the "Properties" button to the right."

- I do have several entries under 'Wireless', all marked as Last Used - Never, but I don't have any "Properties" button, only "Add" "Edit" and "Delete"

---

### Post by Glyn Hughes on 2010-02-05
Sorry to trouble you with all this, this is what I got:

glyn@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
glyn@ubuntu:~$

---

### Post by ikt on 2010-02-06
> **Glyn Hughes said:**
> 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

>>> [https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

---

### Post by Glyn Hughes on 2010-02-06
Thank you Ikt for that - I tried it with the best care I could, and it did simply nothing at all.

I notice that a whole lot of threads have now appeared asking pretty much the same question, I wonder if anyone has actually succeeded in making it work?

---

### Post by ikt on 2010-02-06
> **Glyn Hughes said:**
> I notice that a whole lot of threads have now appeared asking pretty much the same question, I wonder if anyone has actually succeeded in making it work?

This has been a lesson for me, I'm about to purchase new computer parts and since ubuntu has worked flawlessly on all the computers I have I thought hardware support was fairly decent, I'll be sure to make sure all the hardware works before purchasing.

Are you able to connect to a wireless ap that is unsecured?

---

### Post by Glyn Hughes on 2010-02-06
Dear Ikt, that is a very good question? Can I connect to an unsecured wireless?

I'll hop in my car and go down the road to what is universally accepted as the [worst roadside services known]("http://www.motorwayservices.info/area.php?area=116&show=photos"), where I think they have an unsecured thingy.

Thanks

---

### Post by bkratz on 2010-02-06
Try this link, this person says they have a solution

[http://ubuntuforums.org/showthread.php?t=1367871&highlight=8172](http://ubuntuforums.org/showthread.php?t=1367871&highlight=8172)

---

### Post by Glyn Hughes on 2010-02-06
No, that one doesn't work either.

---

