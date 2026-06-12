---
title: "can someone tell me how t configure my wireless card??"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by cranky1984 on 2009-03-11
Hello all,

After weeks of consideration and thinking and rethinking and lotsa friendly advice from fellow Ubuntites, I finally took off vista ( it was being a pain in the wrong place..:D) and installed xp pro sp2 (needed it for some of my apps) and Ubuntu 8.1 ( Im loving it:KS).

SInce im an absolute newbie to linux, im not very sure how to check if everythings working fine. 
1>My wireless card doesnt work, so do I need to download some drivers for my wireless card?
2> is there some software which would give me an overview if the rest of the hardware is working fine?

Id be obliged if you guys could help me out..:) THanks in advance.

My configuration is as under:-
AMD AthlonTM 64 X2 Dual-Core processor TK-57 (1.9GHz/256KB)
2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 Dimm
ATI Radeon® Xpress 1150 256MB HyperMemory&#33922; (integrated)
120GB 5400RPM Hard Drive
8X DVD+/-RW with double-layer DVD+R write capability, Cyberlink Power DVD
Integrated Audio
Dell Wireless 1490 802.11a/g Wi-Fi Internal Card

---

### Post by avtolle on 2009-03-11
What chipset does your wireless card use? From a terminal (Applications>Accessories>Terminal) do```
lspci
```and post the output for review. 

If, as I suspect, said wireless card had a Broadcom chipset, see [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice)) for some information. Also, are there any drivers in System>Administration>Hardware Drivers for the card which need activation?

---

### Post by cranky1984 on 2009-03-11
hey...i ran lspci and this is the output i got.


cranky@cranky-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
cranky@cranky-laptop:~$

---

### Post by bailbath on 2009-03-11
Here are a couple of links for you hope it helps you.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Ian

---

### Post by cranky1984 on 2009-03-11
I just ran system > administration> hardware drivers and got an option to install drivers for broadcom 43** wireless drivers.
I clicked..it downloaded and installed and then asked me to restart. I did that but it still shows me as unconnected. Is there anyway I can check if the wireless card is working?, I mean like in windows you get to choose the wireless networks from a list of available networks. DO i need to start some application so that the wireless drivers are loaded or something? 
It would be great if someone could help me out with this.

---

### Post by anewguy on 2009-03-11
Do you have network manager installed and running?  Check to see if you have an icon on your upper bar that looks like 1 screen on top of another.  If so, click on it and see if any wireless networks show - this would indicate your card is working.  you can select any of the networks that show and attempt to connect to them, but if they are secured then you must know if wep or wpa, the password or passphrase, etc., before you can connect.

If nothing shows, go to system/administration/network and be sure roaming mode is enabled.

Let us know the status of both of the above.

dave :)

---

### Post by RIT_girl on 2009-03-11
Hi, 

I'm having a similar problem. except I can connect wired. I have eeebuntu standard, so I don't have the network tab under system-administration. So I can see the network manager icon and its running, but I can't view any wireless...

---

### Post by cranky1984 on 2009-03-11
yipeeeeeeeeeeeeeeeeeeeeeeee...
it started working.....
it just had chosen some random network..
and oh btw.all i needed to do was look on the network connection icon and the wireless netwroks were shown and then i could choose it..( jeez....and to think that i couldnt get it...lolol....)
thanks a ton guys for your help....:)

---

### Post by cranky1984 on 2009-03-11
Hey RIT,

That was my same problem too lady.. I could connect wired ethernet..

try doing the lspci on terminal window and that should tell you the wireless card that you have. Go to System> administration> hardware drivers and it will show you the drivers if they are available. If you see your wireless card driver there, click on it and do apply.it might ask you to reboot. do that.

I didnt see any netork tabs under administration either. Try looking at the top right hand corner of your desktop and the network icon should be there. Try clicking on it and if your lucky you might see your wireless networks pop up..good luck

---

### Post by thtrgremlin on 2009-03-11
nm-applet should allow you to browse for wireless networks.

I have had an issue with some computers not installing the broadcom package correctly, and have needed to do it from synaptic.

Try:
```
sudo apt-get install b43-fwcutter bcm5700-source
```

I do not know why it doesn't always work even after it figures out what you need, but the above has worked for me when the hardware drivers tool appears to not quite do it correctly.

Also, just in case, check that in /etc/NetworkManager/nm-system-settings.conf that "Managed" is set to "true".

If nm-applet is not running, you can start it and keep it running without keeping the terminal open with:```
nm-applet & disown && exit
``` to get it going right now, then for the future you can add nm-applet to startup apps in intrepid System->Preferences->Sessions or jaunty System->Preferences->'Startup Applications'. (Same tool, different name)

Best luck.

---

### Post by RIT_girl on 2009-03-11
No luck on looking for the wireless, I'm wondering if my roam is disabled. When I go to look at drivers, nothing shows up...and I'm not sure what wireless card I have. :(

---

### Post by bailbath on 2009-03-11
> **RIT_girl said:**
> Hi, 

I'm having a similar problem. except I can connect wired. I have eeebuntu standard, so I don't have the network tab under system-administration. So I can see the network manager icon and its running, but I can't view any wireless...

I guess you have a eeepc netbook?
They use a different wireless chip
But you better tell us what you got first to make sure.
Ian

---

### Post by RIT_girl on 2009-03-11
I think this is the information you want..

-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:15:af:bc:ee:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless

---

### Post by bailbath on 2009-03-11
Had a little poke around and found this on eeebuntu forum
'Something extraordinarily silly has happened to some users that has kept the wireless from working. Please check out the user settings: System>Users and Groups. Unlock it, click on your user name, and look at the permissions tab. Make sure there is a checkmark next to "Connect to wireless and wired networks."' thanks to stanjam on that forum.

If that is not your problem then someone else may jump in and help you but I don't have a eeepc or use eeebuntu. If no one does maybe worth your while popping over to eeebuntu forum - [http://forum.eeebuntu.org/index.php]("http://forum.eeebuntu.org/index.php")
Ian

---

### Post by RIT_girl on 2009-03-11
That was it, I can't thank you enough! I really appreciate it, I was ready to throw the thing out of the window, it was working yesterday :)

---

### Post by bailbath on 2009-03-11
Well if you ever want to throw it out the window again you can always throw it through mine (Please make sure it's open;))
Ian

---

### Post by anewguy on 2009-03-11
Just to clarify - when you go to system/administration/network, you have to highlight the wireless entry and then go to the general (I think) tab to find the roaming mode toggle.  You may have to click "unlock" and enter your password before it will let you do that.

Dave :)

---

### Post by anewguy on 2009-03-11
> **cranky1984 said:**
> yipeeeeeeeeeeeeeeeeeeeeeeee...
it started working.....
it just had chosen some random network..
and oh btw.all i needed to do was look on the network connection icon and the wireless netwroks were shown and then i could choose it..( jeez....and to think that i couldnt get it...lolol....)
thanks a ton guys for your help....:)

We all learn somehow (for me, it's usually the hard way! :) ).  At any rate, glad to have been of help.

Dave :)

---

### Post by anewguy on 2009-03-13
> **bailbath said:**
> Well if you ever want to throw it out the window again you can always throw it through mine (Please make sure it's open;))
Ian

I agree - if anyone out there is getting ready to shoot, throw out the window, hit with a hammer, etc., their computer equipment, you can just ship it to me.  I'll be sure to "destroy" it for you!  :P


Dave :)

---

