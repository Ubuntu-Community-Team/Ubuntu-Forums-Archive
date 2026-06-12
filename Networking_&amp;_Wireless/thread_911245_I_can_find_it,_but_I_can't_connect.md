---
title: "I can find it, but I can't connect"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by vidunderpulver on 2008-09-05
Hi, I did loads of stuff to make my wireless work on my Asus F5R, well... I can find the network now, but I can't seem to connect to it...

Thank you for your help =)

---

### Post by knix on 2008-09-05
try 
sudo iwlist scan
sudo iwconfig wlan0 (or eth1, etc.) essid any
  replace wlan0 with whatever your wireless card is
  replace any with your network name (in quotes if it has spaces)
  add key ##### if it's encrypted (replace ##### with your key
iwconfig (see if it's associated with an access point)
sudo dhclient (if it's associated)

If it isn't associated, then post your results from sudo lspci, then we'll find you some instructions for your chipset (there should e someone else with the same problem)

---

### Post by vidunderpulver on 2008-09-05
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

---

### Post by vidunderpulver on 2008-09-05
*bump*

---

### Post by vidunderpulver on 2008-09-05
*re-bump*

---

### Post by vidunderpulver on 2008-09-05
*sigh* *re-re-bump*

---

### Post by jimmgunnz on 2008-09-05
heya... i actually have that confounded 4311 jobber too.

i didn't see which driver you're using... i think that can be seen thru lshw -C network

i'm using ndiswrapper now.  i can't connect to networks thru typical roaming mode fashion, unless there's zero encryption.  if it's encrypted, i need to manually configure that network.  try that for starters maybe?

---

### Post by vidunderpulver on 2008-09-05
Right now I'm going to bed, but tomorrow morning I'll post my results from Lshw -C network =)

---

### Post by jimmgunnz on 2008-09-05
okay, just make sure you use a lower case "l" in the lshw =]

otherwise it bashes!

---

### Post by vidunderpulver on 2008-09-06
*-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1b:fc:94:19:f6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1d:60:35:18:06
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair

---

### Post by vidunderpulver on 2008-09-06
*bump*

---

### Post by vidunderpulver on 2008-09-06
*re-bump*

---

### Post by jimmgunnz on 2008-09-06
btw... which version of ubuntu are you using??  

     lsb_release -a

i'm on hardy, 8.04

looks like the driver you're using is a wl driver, which i'm actually not too familiar with.  
the most common drivers i've seen for broadcom, at least for hardy, are the b43 series and ndiswrapper.  
i use the ndiswrapper one.

if you want to try using one of those to see if that works better, you might have more luck?  just make sure you do a rmmod wl so your current driver doesn't conflict with the new driver.

someone else may have more to offer about the specific driver you've already got though...

---

### Post by vidunderpulver on 2008-09-06
Ubuntu 8.04.1

---

### Post by jimmgunnz on 2008-09-06
did you ever try to manually configure the network you're trying to connect to????

---

### Post by tx_2642 on 2008-09-06
hello guys.. i'm here got same prob too.. can i share my prob here..? i'm using laptop gateway T-1616.. i've install ubuntu hardy 8.04.. i've found wifi driver using ndisgtk.. i think that step almost same with ndiswrapper.. but till now i still can't connect to the internet.. but if i use wired.. of couse no prob.. so anybody can help me..? please.. =]

---

### Post by vidunderpulver on 2008-09-06
> **jimmgunnz said:**
> did you ever try to manually configure the network you're trying to connect to????

uhm no, I don't really know how to do that... sorry.

---

### Post by jimmgunnz on 2008-09-06
okay, well you can do it the gui way too i guess.  
but i'm sure some of the code whizzes on here can tell you how to do it that way too.
i'm kinda half n half =]
click on the little computers icon and click manual configuration.
click on wireless connection and click properties.
enter all your stuff and click ok.
you'll just need to know your encryption info.
probably go dhcp and let it configure an ip for you.
then save it as a setting.
hopefully it connects you =]

---

### Post by vidunderpulver on 2008-09-06
what is my encryption info or how do I find it?

EDIT: omg, I'm such a noob *embarrassed*

---

### Post by jimmgunnz on 2008-09-06
yikes...  yeah someone must have that password.
it's usually like 26 characters or something.
i'm not sure how you can get that if you don't know it or someone who knows it.
i'm not *that* much of a hacker =]
maybe someone else might know that?

---

### Post by vidunderpulver on 2008-09-06
Well... My router is just set as default, so I don't know if it's a password on it at all.

---

### Post by jimmgunnz on 2008-09-06
okay, well if it's not encrypted at all...
try enabling roaming mode.
make sure to save it as a setting too.
then left click on your network manager icon and you should see all the networks you can connect to.
pick yours and try to connect.
seems like it should work....
do you even see your wireless connections options in your network manager??

---

### Post by vidunderpulver on 2008-09-07
That's weird, my WEP is disabled, but I still can't connect or find the network...

---

### Post by vidunderpulver on 2008-09-07
Sorry for keeping on bumping this, but I really can't figure this thing out... Sorry...

---

