---
title: "Edgy won't recognize network cards"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by UphillSkier on 2007-04-04
I run a dual boot clone (Windows XP / Ubuntu 6.10) with an integrated ethernet connection and a Linksys wireless WMP45g card. Both were working under Win XP. I never got the wireless connection working under Ubuntu.  I returned from vacation to find the ethernet connection kaput.  I replaced it with a D-link DFE-538TX PCI network card.  Both cards work under Win XP. But Ubuntu can't find either one. I am forced back to win XP for all network communication. It doesn't seem worthwhile struggling more with installing drivers until I can see the cards.  Any help would be gratefully appreciated.  

Here are the details

Windows sysinfo shows the following network cards 

```
# this information obtained from sysinfo under Windows XP

# The wireless card	
Name	[00000010] Linksys Wireless-G PCI Adapter
Adapter Type	Ethernet 802.3
Product Type	Linksys Wireless-G PCI Adapter
Installed	Yes
PNP Device ID	PCI\VEN_1814&DEV_0301&SUBSYS_00551737&REV_00\4&176304AC&0&4899
Last Reset	2007-04-04 20:48
Index	10
Service Name	RT61
IP Address	192.168.1.101
IP Subnet	255.255.255.0
Default IP Gateway	192.168.1.1
DHCP Enabled	Yes
DHCP Server	192.168.1.1
DHCP Lease Expires	2007-04-05 20:48
DHCP Lease Obtained	2007-04-04 20:48
MAC Address	00:16:B6:99:23:40
Memory Address	0xFEAF0000-0xFEAF7FFF
IRQ Channel	IRQ 18
Driver	c:\windows\system32\drivers\rt61.sys (1.00.03.0000, 347.75 KB (356,096 bytes), 2006-08-18 12:07)

# the new NIC card
Name	[00000003] ADMtek AN983 based ethernet adapter
Adapter Type	Not Available
Product Type	ADMtek AN983 based ethernet adapter
Installed	Yes
PNP Device ID	Not Available
Last Reset	2007-04-04 20:48
Index	3
Service Name	AN983
IP Address	192.168.1.101
IP Subnet	255.255.255.0
Default IP Gateway	192.168.1.1
DHCP Enabled	Yes
DHCP Server	192.168.0.1
DHCP Lease Expires	2007-04-09 19:29
DHCP Lease Obtained	2007-04-02 19:29
MAC Address	00:16:B6:99:23:40

```

But lshw --short finds nothing 

```

H/W path                    Device     Class       Description
==============================================================
                                       system      System Product Name
/0                                     bus         P5V800-MX
/0/0                                   memory      BIOS
/0/4                                   processor   Intel(R) Pentium(R) 4 CPU 2.66GHz
/0/4/5                                 memory      L1 cache
/0/4/6                                 memory      L2 cache
/0/4/7                                 memory      L3 cache
/0/25                                  memory      System Memory
/0/25/0                                memory      PartNum0
/0/25/1                                memory      PartNum1
/0/f0000000                            bridge      P4M800CE Host Bridge
/0/f0000000/1                          bridge      VT8237 PCI Bridge
/0/f0000000/1/0                        display     UniChrome Pro IGP
/0/f0000000/f               scsi0      storage     VT8251 AHCI/SATA 4-Port Controller
/0/f0000000/f.1                        storage     VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
/0/f0000000/f.1/0           ide0       bus         IDE Channel 0
/0/f0000000/f.1/0/0         /dev/hda   disk        Maxtor 6L080L0
/0/f0000000/f.1/0/0/1       /dev/hda1  disk        W95 FAT32 partition
/0/f0000000/f.1/0/0/2       /dev/hda2  disk        Linux filesystem partition
/0/f0000000/f.1/0/0/3       /dev/hda3  disk        Extended partition
/0/f0000000/f.1/0/1         /dev/hdb   disk        HL-DT-ST DVDRAM GSA-H10A
/0/f0000000/f.1/0/1/0       /dev/hdb   disk        
/0/f0000000/10                         bus         VT82xxxxx UHCI USB 1.1 Controller
/0/f0000000/10/1            usb1       bus         UHCI Host Controller
/0/f0000000/10/1/1          scsi2      printer     PSC 1600 series
/0/f0000000/10/1/1/0.0.0    /dev/sda   disk        PSC 1610
/0/f0000000/10/1/1/0.0.0/0  /dev/sda   disk        
/0/f0000000/10.1                       bus         VT82xxxxx UHCI USB 1.1 Controller
/0/f0000000/10.1/1          usb2       bus         UHCI Host Controller
/0/f0000000/10.2                       bus         VT82xxxxx UHCI USB 1.1 Controller
/0/f0000000/10.2/1          usb3       bus         UHCI Host Controller
/0/f0000000/10.3                       bus         VT82xxxxx UHCI USB 1.1 Controller
/0/f0000000/10.3/1          usb4       bus         UHCI Host Controller
/0/f0000000/10.4                       bus         USB 2.0
/0/f0000000/10.4/1          usb5       bus         EHCI Host Controller
/0/f0000000/11                         bridge      VT8251 PCI to ISA Bridge
/0/f0000000/13                         bridge      VT8251 PCI to PCIE Bridge
/0/f0000000/13/0                       bridge      VT8251 PCIE Root Port
/0/f0000000/13/0.1                     bridge      VT8251 PCIE Root Port
/0/f0000000/13/1                       multimedia  VIA High Definition Audio Controller
/0/f0000000/13.1                       bridge      VT8251 PCI to PCI Bridge
/0/100                                 bridge      P4M800CE Host Bridge
/0/101                                 bridge      P4M800CE Host Bridge
/0/102                                 bridge      PT890 Host Bridge
/0/103                                 bridge      P4M800CE Host Bridge
/0/104                                 bridge      P4M800CE Host Bridge
/0/105                                 bridge      VT8251 Ultra VLINK Controller

```

Here is the complete lshw output:  [ATTACH]28996[/ATTACH]

lspci can' t find anything either:  [ATTACH]28994[/ATTACH]

---

### Post by scrooge_74 on 2007-04-05
Next time you go shopping for parts remember to check first if there are drivers for linux.

Try using nsdiswrapper

---

### Post by UphillSkier on 2007-04-05
> **scrooge_74 said:**
> Next time you go shopping for parts remember to check first if there are drivers for linux.
Try using nsdiswrapper

I am really not very technologically advanced, but I don't think the driver is the issue
 
   first because the wireless card uses an RaLink rt61 driver which is known to work in linux ( see there is extensive discussion of  this in the forum, see [http://ubuntuforums.org/showthread.php?t=132980&highlight=ralink+rt61+wireless+solved](http://ubuntuforums.org/showthread.php?t=132980&highlight=ralink+rt61+wireless+solved))
   
and second because most  driver installation procedures I have seen begin by using lspci or lshw   to see whether the card is recognized.

Can someone confirm that I am right about this?

---

### Post by kyokikun on 2007-04-05
Just putting in my two cents on this, ran into this problem as well. I had kubuntu on my laptop running edgy 6.10 and was able to connect wireless after i downloaded some networking packages and tranfered them to my machine. It has a program that helps connecting to wireless and makes it simple to do. Had a problem with it sometimes that it wouldnt connect just had to try a few times. I got rid of kubuntu and installed ubuntu 6.10 and for the love of god i couldnt get wireless working at all. It showed it knew my card but wouldnt connect. I have a Intel PRO/Wireless 3945ABG installed in my machine. So when i was able to get home and hard line it i had connection and updated my linux and it had 170 roughly i belive updates. Installed them and still couldnt connect to the internet. At work i was able to connect again through a hard line and went to add/remove and searched up the kde wireless program. Now i loaded it up and it showed 0 signal but it did show the hidden wireless my work has but that has a password. I am unable to see if it works yet i still have 3 hours left before school to check it out. But if it does work ill get back on and give the name of the program.

so i belive just update your system and install the kde wireless program that might work. So i am hoping to find out soon enough, and i hope that will help with your issue as well. I think its just edgy messing up on its networking packages.

---

### Post by UphillSkier on 2007-04-05
Thanks for the ideas and I hope your program works.  My system is reasonably up to date (all updates installed except for the past two weeks).  I suppose I could try Feisty Fawn beta or wait for the production release 19 April.

---

### Post by kyokikun on 2007-04-05
also i was just reading on some other threads that for 6.10 you need to go into networking and deactivate your cards then go into the other networking tool to connect. Not sure how that works but try that as well gonna try that when i can get to school.

---

### Post by jdmpike on 2007-04-05
All,

I am having the same problem.

I am running an up-to-date Kubuntu 6.10 system and it is unable to detect the WMP54Gv4 card that I installed in to two different PCI slots in my computer. I have **not** confirmed that the card isn't dead by trying it under windows, etc.

The output of lspci is below:

```

jordan@luckyone:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX5200] (rev a1)

```

When I run ifconfig, I only get entries for eth0 and lo, so nothing is showing up there either (Nor would I expect it to...).

Finally, I agree that this not a problem with configuring software to get the card connected to the router. I believe the cards are either 1) dead, or 2) we are loading the wrong modules and that is preventing the cards from being detected.

**Can anyone recommend steps to help determine a way to get the WMP54g v4 to show up in lspci and ifconfig?**

Once we get that working, we will be able to communicate with the card using iwconfig, wpa_supplicant, or whatever GUI tool we want. The pre-requisite step is getting the system to see the card though.

Very best regards,

jdmpike

---

### Post by UphillSkier on 2007-04-05
> **jdmpike said:**
> All,

<snip>
**Can anyone recommend steps to help determine a way to get the WMP54g v4 to show up in lspci and ifconfig?**

jdmpike

Thanks, jdmpike.  Nice to know I'm not alone.  You have put our question very clearly.

best wishes
UphillSkier

---

### Post by jdmpike on 2007-04-05
After talking to some folks in my local Linux Users Group, they suggested booting into a live cd of a non-debian based distro to see if it recognizes the card (something like suse, mandravia, or fedora).

I also heard feedback in #kubuntu saying that 'upgrading to fiesty solved lots of kernel related issues'. I also might give that a shot since the machine I am working on is pretty much a clean image.

Tonight when I get home, I will let you know how it works out.

-jdmpike

---

### Post by jdmpike on 2007-04-06
All,

I think my card is just dead. Simple as that. I am going to take it back and get the same model, different card. If that one doesn't show up, then I will blame the way modules are being loaded and buy a wireless internet gateway.

Btw, Feisty (kubuntu) is really, really nice. I am a big fan! Way to go everyone who contributed.

Peace, love, ubuntu,

jdmpike

---

### Post by jdmpike on 2007-04-07
Just tried my second WMP54G v4 card and nothing... it still isn't detected with lspci...

I really don't think that both of these cards are dead...

Does anyone have any idea what might be going on?

-jdmpike

---

### Post by jdmpike on 2007-04-07
Okay, so I decided to change slots and really jammed that sucker in the PCI slot... Good thing I have been working out I guess.,,

viola!

```

01:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 22
        Memory at fc9fc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

```

... now all I have to do is get it connected to my router via WPA2.

Best regards all,

jdmpike

---

### Post by UphillSkier on 2007-04-08
Glad you're on the way, jdmpike.  I'm still stuck, but I am beginning to think there is a serious problem with my motherboard.  I tried to boot from a live CD, as suggested by your linux group, but nothing works. 

Mandriva-one-2007-kde1-iso fails to boot to the kde desktop. Instead it boots "non-interactively", stalls after "loading HAL daemon" and resumes at a login prompt after I hit enter.  Startx returns a fatal error ("no screens found").  

An old version of knoppix (2005) , which used to work, just stalls at the first penguin logo. 

I can still boot up to the installed version of edgy, but can't see any network card (no eth0, no ra0).  I am trying to find my installation disk for Edgy to see if the live CD version still works.  

In the meantime Windows XP boots fine and connects to both the ethernet and the wireless  card. My wife says why don't I stop skiing uphill and embrace windows? I don't want to admit defeat, but she may have a point.  

Guess I'll wait until I try the edgy live cd before deciding what to do next. :cry:

---

### Post by UphillSkier on 2007-04-08
Success!  I guess I can continue to ski uphill for a while longer.:) 

The Edgy live CD didn't find the network cards, but the Feisty Fawn Beta did! I am writing this from the live CD version.  What on earth was going on in Edgy, I wonder, that could make it fail to see PNP cards? 

Does anybody have advice on installing the beta vs waiting for the feisty release?  Is there a release candidate coming out soon?

Best wishes to all
UnphillSkier

---

