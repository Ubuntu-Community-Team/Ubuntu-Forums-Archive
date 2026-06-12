---
title: "AR242x Not working in Hardy"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by logrusmage on 2008-04-24
So here's the deal: I can't even get it to search for wireless networks.

I've enabled the3 restrictive driver. And it appears to detect the internal card, it just won't let me do anything wireless wise.

Here are the results for lshw -C network
> PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:06:24:86
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.108 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


And the results for iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.


And here are my lspci results

> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


I appreciate any help I can get. I really don't want to have to switch back to Windows or to buy a new external wireless card for my new laptop. 

Oh! And I can't seem to update! It gives me an error and about half of the packages cannot download, seems to be all of the translation packages aren't coming through :(.

Help?

---

### Post by logrusmage on 2008-04-25
Ok this is ridiculous. I can't get any of the ******* drivers because it can't update. It says it will omit the packages that are failing if they continue to fail but it NEVER DOES.

What the hell man? Ugh. This is seriously killing me...

Every time I try to download ANY package in the terminal I get the "cannot find package" error. EVERY TIME. It's driving me crazy.

Well I figured SOMETHING out... I cannot connect to us.archive.ubuntu.com for some reason... arg....

Edit: Heres my error for apt-get update -
>  sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


---

### Post by ameseisch on 2008-04-26
My compaq presario F700 has the same card, and similar issues. The card is detected and "in use" in the drivers menu, however, no options to do ANYTHING with the wireless connection. as though its not really there. On this laptop there is a switch to turn the wireless on and off and it won't switch on (the light turns blue when it is on.) i suspect if i could magically make it turn on that might help.

a lot of people have had problems with the atheros drivers. why do i pick laptops with incompatible drivers? the last one was a broadcom on a dell that fought me like crazy!

I had a similar issue with updates... figured might just be servers being overloaded with new release.

disappointed overall with new Ubuntu. For a laptop to be useful it needs wireless. so basically Ubuntu renders my laptop useless. sad that i might have to go bad to vista, i didn't like it and it sucks in a number of ways, but at least it worked, ...

---

### Post by ameseisch on 2008-04-26
Looks like these boards are somewhat overwhelmed with wireless card issues... bummer. this issue is beyond any help I can offer, so I am really hoping someone can help with this. By the way the ndiswrapper method did not work for this one. 

is there anyway to manually turn on the wireless card from the terminal or something?

---

### Post by ameseisch on 2008-05-08
So this issue was answered in another post. Aparently hardy mis detects this card. it is really a atheros 5007eg or something. that is the driver you need. and you have to disable the ones in the hardware manager.

---

### Post by gar2feed on 2008-07-26
I have the same problem ( ar242x) i have looked everywhere and tried a hundred different downloads, fixes, packages etc. the trouble shooting only gets me so far. i have hit dead end after dead end. why release a product (ubunto) if the bugs are not fixed yet? not a good way to promote linux.#-o im about fed up with all these so called fixes and driver downloads that do nothing!

---

### Post by jualin on 2008-08-03
[There is improvement in this thread]("http://ubuntuforums.org/showthread.php?t=878148"). The person is being able to connect with the network, therefore the correct drivers were found.

---

### Post by walkerk on 2008-08-03
You could always use [ndiswrapper]("http://ndiswrapper.sourceforge.net"). This will let you use the Windows driver for the Atheros chip. I have this same card and I searched for help and soon realized it would be a pain. So, I didn't even bother with native drivers... My wireless was working within 10 minutes of loading 8.04 on a newly purchased laptop.

---

### Post by jualin on 2008-08-03
> **walkerk said:**
> You could always use [ndiswrapper]("http://ndiswrapper.sourceforge.net"). This will let you use the Windows driver for the Atheros chip. I have this same card and I searched for help and soon realized it would be a pain. So, I didn't even bother with native drivers... My wireless was working within 10 minutes of loading 8.04 on a newly purchased laptop.

That's exactly the procedure that the person on the other thread used. For any chance are you using a 64 bit processor, because I am trying to help out someone who got everything to work but when he restarts the computer he loses configuration and has to reinstall the driver again. Maybe you can check that my suggestions are accurate since you already made this card to work on Hardy.

---

### Post by epiphonygirl on 2008-08-04
You may also want to doublecheck in windows and make sure that your card is an AR242x, I just recently had Hardy misidentify my card as this when really its an AR5211. To do this you have to boot into windows for a minute and go start>control panel>system>choose hardware tab>click device manager>open network adapters (+)>right click on wireless adapter choose properties>driver tab>click driver details then look at the driver files it should say something like C:\WINDOWS\system32\DRIVERS\[COLOR="Red"]arXXXX[/COLOR].sys what's in red is the driver that you're using and supposed to use. Its not that I don't trust Hardy, its just that it can misidentify the card.

---

### Post by IndyGunFreak on 2008-08-14
> **gar2feed said:**
> I have the same problem ( ar242x) i have looked everywhere and tried a hundred different downloads, fixes, packages etc. the trouble shooting only gets me so far. i have hit dead end after dead end. why release a product (ubunto) if the bugs are not fixed yet? not a good way to promote linux.#-o im about fed up with all these so called fixes and driver downloads that do nothing!

You should learn what a bug is... This is not a bug.

There are 100's of instructions via google to get this device to work in about 2min.  I've had this device working w/ madwifi for several months.

---

