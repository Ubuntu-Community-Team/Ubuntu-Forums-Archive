---
title: "RTL 8187B Wireless Problems"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Andrej_Schoeke on 2007-09-09
Hello,

I installed Ubuntu Feisty Fawn (7.04) on a notebook. Actually, almost everything works, but what really bothers me is that the WLAN-NIC is not working. Under Vista   it is designated as a RTL8187B.

So, here is the standard output of lshw, lspci and lsusb (relevant parts only):

lshw:
```
     *-usb:2 UNCLAIMED
                   description: Generic USB device
                   product: RTL8187B_WLAN_Adapter
                   vendor: Manufacturer_Realtek
                   physical id: 8
                   bus info: usb@5:8
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
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
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
0a:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

lsusb:
```
Bus 005 Device 004: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 005 Device 002: ID 064e:a100 Suyin Corp. 
Bus 005 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

I found with sudo modprobe -l amodule called rtl8187 but that did not help. So, iwconfig still doesn't show a wlan device and ifconfig wlan0 up does also end with an error message.

[edit] Oh, btw, this is not USB thing.It is integrated in the notebook, as it would be a pci card.

Any suggestions?

---

### Post by kevdog on 2007-09-09
ndiswrapper + win98 driver for installation :)

---

### Post by Andrej_Schoeke on 2007-09-09
Actually I found out that there is a linux nativ driver and it is in the 2.6.23 kernel (atleast that a version where I am sure, will provide link later). Is there an easy and convenient way to get a 2.6.23 ububtu system?

Thanks, for the answer, but I don't like the ndiswrapper solutions somewhat. It is a workaround, but not a good one... :-/

---

### Post by Spear on 2007-09-09
Hi, there's a realtek driver in the basic Feisty 7.04 ... it's name is r818x.

I own a german Allnet Wifi pci basic board, but the All 0261 seem to hold Marvell, Atheros or, in my case, Realtek chipset, depending on ... i don't know what ;) ...

try :

modprobe r818x

and then, tell us if it changes the result with iwconfig command ?

---

### Post by Andrej_Schoeke on 2007-09-09
> **Spear said:**
> Hi, there's a realtek driver in the basic Feisty 7.04 ... it's name is r818x.

I own a german Allnet Wifi pci basic board, but the All 0261 seem to hold Marvell, Atheros or, in my case, Realtek chipset, depending on ... i don't know what ;) ...


^^
> 
try :

modprobe r818x

and then, tell us if it changes the result with iwconfig command ?

Nope, not with the iwconfig. Messages also suggest nothng new, but ifconfig register a new device called ng.
hmmm. Any suggestions?

ps: [Link to 2.6.23RC thread]("http://www.debianforum.de/forum/viewtopic.php?p=555193")

---

### Post by Andrej_Schoeke on 2007-09-09
I looked into the messages to see whether  or not the chipset is the right.

```
Sep  9 21:05:49 linis kernel: [  848.556000] 
Sep  9 21:05:49 linis kernel: [  848.556000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
Sep  9 21:05:49 linis kernel: [  848.556000] Copyright (c) 2004-2005, Andrea Merello
Sep  9 21:05:49 linis kernel: [  848.556000] rtl8180: Initializing module
Sep  9 21:05:49 linis kernel: [  848.556000] rtl8180: Wireless extensions version 21
Sep  9 21:05:49 linis kernel: [  848.556000] rtl8180: Initializing proc filesystem

```

That's all. From other entries, I can see, that a lot more should be done, which implies, that it is plain the wrong driver... Strange.

For the module rtl8187, it is even more sparse:

```

Sep  9 21:11:50 linis kernel: [ 1209.472000] usbcore: registered new interface driver rtl8187

```

---

### Post by bigmista on 2007-09-20
Have there been any developments on this? I have a Gateway MX8739 laptop with the same wireless chipset and I am having the same problem.

---

### Post by virtualXTC on 2007-09-20
> **bigmista said:**
> Have there been any developments on this? I have a Gateway MX8739 laptop with the same wireless chipset and I am having the same problem.

As far as I can tell, unless you want to revert to a 2.6.18 kernel, it still doesn't work.  The issue is still the kernel code change as of 2.6.19:

[http://ubuntuforums.org/showthread.php?t=383504](http://ubuntuforums.org/showthread.php?t=383504)

I'm running dual boot 64 bit windows / gnewsense system, and it doesn't look like this puppy will run on either so it's headed back to MicroCenter.

---

### Post by Bob Allen on 2007-09-25
> **kevdog said:**
> ndiswrapper + win98 driver for installation :)

I used Ndiswrapper and the Win 98 driver as Kevdog suggested and everything worked great on the initial installation, but after a re-boot the card would not work. Turns out there is another driver in the Kernal named r8187 and when I blacklisted it everything worked and has been working.

---

### Post by wirelessmonkey on 2007-09-25
There is a native install for the rtl8187 driver.... rtl-wifi.sourceforge.net 
Do the mac80211 install.

---

### Post by cubdukat on 2007-10-09
I have the same laptop and I was forced to do the ndiswrapper/Win98 method. The last drivers I grabbed off of the RealTek website still don't compile, and I haven't seen any newer ones. 
The main disadvantage to using the ndiswrapper method is that it slows down the bootup. I suspect that a natively-compiled driver would probably speed things up.
Guess I'll wait and see what happens with Gutsy Gibbon.

---

### Post by kevdog on 2007-10-09
So why dont you just use the native drivers compiled into the Feisty kernel??  The r8187 driver..

---

### Post by panurge77 on 2007-10-10
Native driver hangs at high traffic, most likely when uploading. Ndiswrapper is not slowing my boot here. Did you add it to /etc/modules?

The problem I have is wpa will not start at boot, I have to do it manually. Wep works, though. Anyone got wpa at boot with ndiswrapper?

---

### Post by kevdog on 2007-10-10
WPA works with me with ndiswrapper on boot - however Im not usng a rtl card rather than a broadcom card.  Do you have a link where you got the win98 driver for your card??

---

### Post by panurge77 on 2007-10-10
Ye. Here it is:
[http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html](http://www.majorgeeks.com/Realtek_RTL8187_USB_Wireless_LAN_ME2000XP_d5165.html)

How did you configure your connection?

---

### Post by kevdog on 2007-10-10
I use WICD setting the WICD daemon to start at boot which then brings the interface up automatically.

I suppose you could also do this in a script and bring the network up manually.  You would either need to inject this script to the appropriate run level file, and put it into system->pref->sessions.

My guess is that why its not working for you is that some service hasnt been initialized when your networking script runs.

---

### Post by panurge77 on 2007-10-10
I dont know, I haven't really looked into it yet, but it could be something simpler and tricky. When I used rtl8180, I had to edit etc/network/interfaces so the password would be set before the essid and that solved it all, but that was wep. 

I'm not really bothered by having to set the network manually because I don't reboot the box everyday, but I'll post the solution on my rtl8187 how-to when I find it out.

---

### Post by kevdog on 2007-10-11
panurge - is this link for the 8187 driver specifically or for the more general 818x driver for 8180 and 8185 and 8189 varieties??

---

### Post by cubdukat on 2007-10-12
> **kevdog said:**
> So why dont you just use the native drivers compiled into the Feisty kernel??  The r8187 driver..

Not to put too fine a point on it, but they plain don't work.

---

### Post by kevdog on 2007-10-12
See the following link: They do -- with some minor twist

[http://ubuntuforums.org/showthread.php?t=567505](http://ubuntuforums.org/showthread.php?t=567505)

---

### Post by panurge77 on 2007-10-14
> **kevdog said:**
> So why dont you just use the native drivers compiled into the Feisty kernel??  The r8187 driver..

I just now realize mine is 8187L. So the driver might be different from 8187B.

---

### Post by kevdog on 2007-10-14
Maybe the hardware on the cards are different, but its the same built-in statically linked kernel module.  I dont know however if it hangs on long downloads.  Again based solely on the information you have provided Panurge, I recommend ndiswrapper.  However, when someone states the built-in drivers do not work, that is plainly not true.  I wonder if anything will change with Gutsy's new kernel.  Personally Im using vanilla kernel (beyond Gutsy's kernel), but I dont have a wireless rtl card to see if this behaivor exists in newer kernel versions.

---

### Post by doon on 2007-10-26
thenk:)

---

### Post by dougtron on 2007-10-28
There has been progress on this internal wireless card (the RTL8187B). No one has made a comprehensive short post about it, but I will give you a link to the thread where we got it figured out. On the last page or the one before that you will see that we discovered a modified driver for the wireless card. 

[http://ubuntuforums.org/showthread.php?t=571046]("http://ubuntuforums.org/showthread.php?t=571046")

PM me if you need help finding the modified driver, otherwise there is sort of support still happening in that thread for anyone who is still strugling with this tricky card.

There ya go!
Doug

---

### Post by kevdog on 2007-10-28
doughtron

I see you got the card up and running.  If you could write this up as a formal how-to it would be fantastic.

On xcuervo's website, the instructions were a little vague.  Id like to link to your howto if possible.

---

### Post by dougtron on 2007-10-28
Yeah I really need to get around to doing that, hopefully later on today I will have some time and write that up. I'm still a little new to this forum...Where would I post it? In the Networking and Wireless section? Anyway I'll work on that and link back to you when it's done.

---

### Post by kevdog on 2007-10-28
Submit it to Networking and Wireless, and if everything looks good, submit it to Tutorials and Tips. Title it How To:  ---------   Fill in the blank.  Instructional posts are a lot easier to find if labeled how to.

---

### Post by Orkun Sensebat on 2008-01-01
try
[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

it does not support wpa and link quality, gets easily compiled and wep works with network manager(with ndiswrapper you have to use iwconfig instead of /etc/network/interfaces).

As this version is not working properly and for sure does not get developed any further by realtek i strongly recommend using ndiswrapper.

another approach could be [http://rtl-wifi.sourceforge.net/](http://rtl-wifi.sourceforge.net/) - which i never tried, since ndiswrapper works perfect.

---

