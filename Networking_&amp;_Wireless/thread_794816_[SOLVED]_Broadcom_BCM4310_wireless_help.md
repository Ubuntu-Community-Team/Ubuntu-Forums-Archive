---
title: "[SOLVED] Broadcom BCM4310 wireless help"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by SurferGTO on 2008-05-15
As many threads as i've been researching this on I've seen nearly zero regarding this specific driver, let alone any success with it.  I've tried all of the walkthru's using NDISWRAPPER and all of that seems to install just fine. I have used the suggested drivers in most of the walkthrus, as well as the drivers on HP's sight for both Vista and XP. As far as I can tell they have all installed fine, and i was able to get ndiswrapper to find the installed driver, but not the actual hardware itself.

i had worked on this a bit in this thread: [http://ubuntuforums.org/showthread.php?t=790890&page=2]("http://ubuntuforums.org/showthread.php?t=790890&page=2") however since that was for the 4311 and this is specifically for the 4310 i figured id start a new thread with hopes of more specified answers.

HP Pavilion dv2745se Notebook PC using the Hardy upgrade, originally off a gutsy disc. never had wireless working. ever.

lspci lists:
> master@master-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
master@master-laptop:~$ 


system>admin>windows wireless drivers shows the driver installed, hardware present: no. 

same results on any driver ive tried thus far. exactly. ive GOT to be doing something wrong myself.

I am a bit new to this but i grasp this stuff pretty quickly. i cant hold a conversation in programming but i definately can follow directions.

---

### Post by Jimmey on 2008-05-15
Can't help you that much because I'm at college at the moment.

The way I got by bcm43xx card working was to - 

Download and install the "bcm43xx-fwcutter" package and use it to retrieve the firmware from the suggested driver "wlapsta.o" (I can't remember where to get this from, I found my information at linuxwireless.org). I then put all the firmware files in /lib/firmware.

You might need to blacklist the ndiswrapper module by making an entry for it in /etc/modprobe.d/blacklist, to stop it loading at boot.

Then, I restarted the computer, and entered the command
```
sudo modprobe -r b43 && sudo modprobe bcm43xx
``` in the terminal.

Note that network manager probably won't report your wireless network card (I believe that to be a bug). You can check that it's worked by entering the command
```
iwconfig
``` in the terminal. If that reports your network card as having wireless extensions, then it has worked.

Unfortunately, the only way I figured to configure the network card from that point was manually. I can't specifically remember how I managed to revert from network-manager controlled wireless to configuration file controlled. To be able to configure your card from that point, some useful commands are

iwlist scan
iwconfig
ifconfig

Entering each of those commands into the terminal, prefixed by "man" (eg "man iwconfig") should prove useful.

Hopefully that works for you.

---

### Post by superprash2003 on 2008-05-15
if that doesnt work you could try these [http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html) some steps require internet though which you could probably get using your wired connection

---

### Post by Ayuthia on 2008-05-15
> **SurferGTO said:**
> As many threads as i've been researching this on I've seen nearly zero regarding this specific driver, let alone any success with it.  I've tried all of the walkthru's using NDISWRAPPER and all of that seems to install just fine. I have used the suggested drivers in most of the walkthrus, as well as the drivers on HP's sight for both Vista and XP. As far as I can tell they have all installed fine, and i was able to get ndiswrapper to find the installed driver, but not the actual hardware itself.

i had worked on this a bit in this thread: [http://ubuntuforums.org/showthread.php?t=790890&page=2]("http://ubuntuforums.org/showthread.php?t=790890&page=2") however since that was for the 4311 and this is specifically for the 4310 i figured id start a new thread with hopes of more specified answers.

HP Pavilion dv2745se Notebook PC using the Hardy upgrade, originally off a gutsy disc. never had wireless working. ever.

lspci lists:


system>admin>windows wireless drivers shows the driver installed, hardware present: no. 

same results on any driver ive tried thus far. exactly. ive GOT to be doing something wrong myself.

I am a bit new to this but i grasp this stuff pretty quickly. i cant hold a conversation in programming but i definately can follow directions.

Going back to the post on the 4311 thread, you said that you ran them in wine.  That should have created a folder that contained the bcmwl5.inf, bcmwl5.sys and bcmwl564.sys(should be in a folder labled sp36684.  Those are the files that you need.  You will need to install bcmwl5.inf.  Please be sure that the *.sys files are in the same directory as the bcmwl5.inf file or else the install will not go correctly.  I am not for sure about how the Windows wireless drivers program works because I generally work from the Terminal, but I am guessing that you can remove the old driver and replace it with the new.

As for the recommendations from the other two posters, they recommend using the depreciated driver.  I don't have much information about your card and bcm43xx, but if you know that it worked in Gutsy or any older versions, feel free to try it out.  When I was searching for information about your card, it seemed that people in Gutsy used NDISwrapper.  As for the b43 driver, I have not seen any official word that it does not work, but all the threads that I have seen with this card has pointed towards NDISwrapper.  Someone in the bcm43xx/b43 mailing list mentioned that it was not supported yet and none of the developers corrected the individual.

Jimmey and superprash2003- If either one of you have this 4310 card (14e4:4315), please let me know.  I would like to know if it does work with bcm43xx.

---

### Post by SurferGTO on 2008-05-15
Ayuthia, from what ive seen i do think you are right. the ONLY two successful installs of BCM4310 (14e4:4315) i had ever read about was using ndiswrapper. not to say it bcm43xx doesnt work though. I personally dont think i had ever tried it while in gutsy, but i may have. i have tried so many different options i actually forget what ive already done. 

i havent had wireless at all ever while using ubuntu. gutsy or hardy. ive been using a usb verizon air card modem and kppp, or a wired connection. im going to try toying around with either the XP and VISTA drivers. 

would all of the driver files be named bcmwl564 (.inf/.sys) regardless of what version or where i got them from?  

and as far as i know, i may be wrong, but i was under the impression that windows wireless drivers was the graphical UI for ndiswrapper in hardy? It wasnt in Gutsy..

---

### Post by SurferGTO on 2008-05-15
ok still same results. The driver installs no problem at all however the hardware itself isnt being recognized by any of the apps/programs. Ive checked this out but cant seem to find anything... a while ago for some reason i remember at one point having to internally turn the card on or something using a script? like right now its off inside the laptop? I might be making that up... i dont know. 

there has to be a way to make the card present. im not having a problem with ndiswrapper or the driver. its apparently the card itself...

---

### Post by Ayuthia on 2008-05-15
> **SurferGTO said:**
> 

would all of the driver files be named bcmwl564 (.inf/.sys) regardless of what version or where i got them from?  Yes.

> and as far as i know, i may be wrong, but i was under the impression that windows wireless drivers was the graphical UI for ndiswrapper in hardy? It wasnt in Gutsy..It is the graphical UI for ndiswrapper.  I think that you had to install it manually in Gutsy, but I am not for sure.  I know that the graphical version was buggy, but that was a while back.  Now it sounds like it is working well.

Oddly enough, I was reading another post on how to remove ssb and it reminded me of a hack that was done for your chipset.  I just found the link and it sounds like the same problem that you had.  Hopefully this will work:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

---

### Post by Jimmey on 2008-05-15
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182716)
That might be useful for you.

---

### Post by SurferGTO on 2008-05-15
holy freakin crap it worked!! 

> Oddly enough, I was reading another post on how to remove ssb and it reminded me of a hack that was done for your chipset. I just found the link and it sounds like the same problem that you had. Hopefully this will work:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

the hack linked to was exactly what i needed to do. now it has wireless as a connection option and my blue light for wireless connection is working!!!  again the link above got everything to work, apparently.

now... Since ive never gotten this far and i have no experiencce what so ever in the rest of the setup... now what. i still cant "connect" to the wireless network shown... i guess i have to manually set up the network? I have NO clue how to do that...  I'll search for a way to do that for now unless its something else that someone can direct me to.

or should i use a different wireless manager (wifi-radar)?

---

### Post by SurferGTO on 2008-05-15
so.. i get nowhere in network manager. i installed wifi-radar and it shows 3 networks in my area (home, default, and linksys) but none of them have any signal or its intermittent.. from strong to nothing at all... oh and there is no "connect" button. and if the signal is strong the second i click it it goes to nothing...

---

### Post by Ayuthia on 2008-05-15
I read somewhere that there is a thing that you need to click in Network Manager.  Somewhere there is an option to set it for roaming.  Do you know if that is set?  I am a Kubuntu user so my Network Manager is different.  

You might also try Wicd.  It seems to work well also.  I am using that on one of my laptops.

In theory, we should be able to connect from the Terminal.  You could try to connect to it by:
```
sudo iwconfig wlan0 essid <name>
sudo dhclient wlan0
```
I am not for sure if yours is wlan0 or eth1.  Also, replace <name> with the name of the access point that you are trying to connect.

---

### Post by SurferGTO on 2008-05-15
well... heres what i get with one code...

> master@master-laptop:~$ sudo dhclient wlan0
[sudo] password for master: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:73:e3:c2:b8
Sending on   LPF/wlan0/00:1a:73:e3:c2:b8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



the other one... when you say replace <name> with my access point.. i have no clue what you mean lol.

so far still having no luck at all with wifi-radar. unchecked roaming in network manager, but i dont know any of the setting information in order to set it up (wireless settings ie password type, network password, and the connection settings ie ip address, subnet mask and gateway address.) i know WHAT they are... just not how to find out what i need to type into the network manager...

---

### Post by SurferGTO on 2008-05-15
sweet. WICD worked point and click.

---

### Post by SurferGTO on 2008-05-15
is there any way to have it connect on login?

---

### Post by Ayuthia on 2008-05-15
> **SurferGTO said:**
> is there any way to have it connect on login?

There should be an arrow right by the name  of the access point.  When you click on it, there is an option for it to "automatically connect to this network".

Glad to see it working!!!

---

