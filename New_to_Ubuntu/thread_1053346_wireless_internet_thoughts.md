---
title: "wireless internet thoughts"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-28
hi everybody
just interested to know if i am using my best option for wireless internet connection.
i entered lspci and got the following result:-
```
nigel@ubuntunigellaptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
nigel@ubuntunigellaptop:~$ 
```
these below seem to me to be possible wireless connection devices.  according to wireless connection information i am connecting via an RTL 8187 - would this actually be the:-
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

and also is the 14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) that is next in the list also a wireless internet connection that i could use.
if so, would it be a better (faster, more stable) option and how do i activate it in preference to the RTL8187/8101E/6102E (i assume these are all the same)
thanks very much for any help.
cheers
nigel

---

### Post by anewguy on 2009-01-28
Do you think you have wireless?  According to the list you provided, the Realtek entry would be for an ethernet controller for a wired connection, and the IEEE1394 is a firewire port.  Neither of these would be wireless.  From what shows on the list you provided, there are no wireless devices for internet access.

Are you by chance using a USB device for wireless?

Dave :)

---

### Post by emarkd on 2009-01-28
Seconded.  You can push IP over firewire, but you'd still need some sort of network interface device that supports it.  For instance, you could connect one computer to the internet using a cable modem and then share that connection with your second computer over firewire.

---

### Post by capnthommo on 2009-01-28
hi there guys
ok a little more detail.
i am not connected by wire.  i am using no USB connection device.  i have a wireless router.
according to connection information - as follows
Active Network Connections
Auto BTHomeHub-F386
Interface:             802.11 WiFi (wlan0)
Hardware Address       00:16:**:**:**:BB
Driver                 RTL8187
Speed                  54 Mb/s
Security               WEP

various IP addresses etc

Connection Properties
network device        Ethernet

hmm, interesting!  if i have not wireless then how am i connected to my wireless router.  i get connection even when the home desktop is switched off (completely)
my laptop is only a year old.
so do you know the command to list my wireless devices or whatever?

---

### Post by anewguy on 2009-01-28
The lspci should have shown it.  Try this and post the output back here in a reply:

lshw -C network


As far as you connecting wirelessly - your lspci really does not show a wireless device, hence the question about a USB device.  Unless your ethernet controller is doubling as wireless (still should have shown as such) there is no visible wireless device.

BTW - what does your home desktop have to do with your connection?

Dave :)

---

### Post by capnthommo on 2009-01-28
hi there anewguy
here's the result
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:88:8a:26
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:1c:8a:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 802.11bg
nigel@ubuntunigellaptop:~$ 

```
i mentioned the home desktop because i am on a wireless enabled (at least it used to be so i thought) laptop but the home desktop is connected via a cable to the wireless hub although the laptop connects seemingly regardless of what the desktop is doing so i would have thought that it was not relevant - is that so?
it looks to me as if the rthernat is indeed serving as a wireless interface in some way but i was under the impression that i had wireless capability on this machine - that's what it was sold as when i bought it with windows loaded.
maybe it's a driver issue?
BTW i'm running 8.10 in 64 bit.
thanks loads
nigel

---

### Post by anewguy on 2009-01-29
First I will assume that even though your desktop is hard wired to the router, your laptop has no network cable connected to it?

Next, I really don't see where this is picking up the wireless it has as wlan0.

So, we should take a step back and ask:

What make/model of laptop is it?

This may give us something to research to try to find out.  But in the mean time, back to your original question, neither of the devices listed by lspci are wireless.  This means, in answer to that question, no you can't use them, and then obviously no they won't be faster.

Dave :)

---

### Post by capnthommo on 2009-01-29
hi there anewguy
okay, the laptop.  it is absolutely definitely not a wired connection of any kind that i can see - i am actually on a different floor from the wireless router that connects to the phone line.  the only cable at present is the mains power feed.
the laptop is a Toshiba Equium A210 - 17l (i think it's a final l not 1).
PSAFJE 003003KS

according to the label on the underside the "radio device" is an RT8187B which i thought was RealTek.
that would be all the tech spec i can give you - the manuals are not very 'in depth'.

but i am definitely getting wireless connection somehow to my wireless router/home hub.  i have the signal bar graph on the notification area of the top panel and have added the network connection indicator too and this shows the 2 monitor screens and gives me ntwork info.

i don't understand.
i shall google up some more on the laptop and come back.
cheers
nigel
:-?

---

### Post by anewguy on 2009-01-29
The only information I've been able to find on that laptop is from uk sites - haven't found anything for U.S..

The reviews indicate realtek sound - where yours apparently has ATI Intel hda.  

They claim wireless as well as the ethernet connection, but don't state the model of wireless.  No mention is made of a PCI or mini-PCI wireless card.  I can only assume at this point that it is somehow incorporated with the ethernet controller, but I don't know how.

I really can't find any in-depth details to explain how the wireless is obtained.

At any rate, as stated earlier, in response to your original questions, there is no other wireless on your computer except what you are using.  The ethernet controller is for a wired connection, the IEEE-1394 port is firewire.  If speed seems to be reduced, check to be sure it is doing wireless g @54mbs.  Also check the signal strength and for noise.  If possible, try using the laptop right by the router and see if it changes any.  BTW - is your router capable of wireless g, if not your speed would be reduced because of the router.

don't know what else to tell you.

dave :)

---

### Post by capnthommo on 2009-01-29
hi again anewguy
- sorry, i just killed the reply when i had nearly completed it!
i'll try and remember what i said.

1.  my router/hub is 54Mb/s if thats what you mean by wireless g - the 'connection information' that comes up when i r/click the wireless signal indicator on the panel shows interface as 802.11 WiFi (wlan0)  driver rtl8187  and speed 54 Mb/s

2.  how can i check my ethernet controller is capable of 54Mb/s wireless g (is that what you asked?) - 

3.  there is no noticeable difference in signal strength (75 to 100% usually) regardless of laptops proximity to router.

the only reason the desktop is connected to the router by ethernet cable is that it's own USB wireless device is refusing to cooperate so its the only way that machine can get online.
i was less successful than you in finding information about my laptop - most of what i found was 'there's wireless, but you don't need to worry about how it works'

i feel a charlatan here, it all works but i just wanted to see if i was using my best available option.  other people have serious problems.
i was just unsure if i needed to add any drivers or anything else and if a tactical download or configuration change might improve things.

its mainly that i am a little unsure of wireless internet generally and i had to connect the laptop via cable to get the initial connection and i just 'got it running wirelessly' whether the best way or not.
thanks a lot for your time
nigel

---

### Post by sandyd on 2009-01-29
some computers have an internal wireless card thats plugged into an INTERNAL usb port (or other port, doesn't really matter). that might be why its not shown.\

EDIT: yep, its plugged in via internal usb. just found it in google

---

### Post by capnthommo on 2009-01-29
hi carlee,
thanks for that. 
 so it's all sensible then?  and not the complete lash up i thought i might have created.  i am afraid i like to 'lift the hood and poke my fingers in' and some times i do more damage than good.  afraid i'm too old to change my ways now though!
incidentally, the stuff on previous posts about connecting another pc to router via ethernet cable - i just got its USB wireless connection device fixed (i had stuck it in the wrong socket!) so now the router is working fully wirelessly again (except for phone and power of course).
unless there is anything else anyone can think to add i can call this solved and my mind put at ease.

thanks again to everybody
nigel
:guitar:

---

### Post by anewguy on 2009-01-29
Aaahhhh - that makes more sense!  Just for grins, post back the output of:

sudo lsusb


Curious to see if some device shows there!

Dave :)

---

### Post by capnthommo on 2009-01-29
hi and thanks again anewguy
here it is
```
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nigel@ubuntunigellaptop:~$ 

```
i shall take it that the wireless adapter at Bus 006 Device 003 would be what we were seeking, so that accounts for the 'oddness in the system.
anyway, thanks again for the help.  i think i can assume it's all ok.  as i said above i just wanted to make sure.  think definitely solved now, don't you?
cheers
nigel

---

### Post by anewguy on 2009-01-29
Yep - all solved!

Dave :)

---

