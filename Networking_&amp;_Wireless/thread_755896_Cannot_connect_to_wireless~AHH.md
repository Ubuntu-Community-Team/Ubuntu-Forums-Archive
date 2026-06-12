---
title: "Cannot connect to wireless~AHH"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by swimm3r137@gmail.com on 2008-04-15
So I just installed ubuntu over windows and so far it's GREAT!!  I love the interface, love the programs, love everything, but...........  I cannot get my laptop connected to my att dsl wireless network.  It's a secondary computer, and before with windows, all I did was recognize the wireless network, then enter the network key.  I mean I've messed around with it, but I'm not quite sure what to do, because I was hoping that the "roaming mode" would just detect it.  Maybe I had my hopes up =(  When I click the task bar and it's in roaming mode, theres no wireless networks that show up, so because mu router doesn't pronounce it's name, I assumed I had only two options. (unless theres a way to get ubuntu to detect the wireless network?  On windows it does! ;(  What I've tried is this:
1) "connect to other wireless network"
  a) i enter in network name
   b) wireless security>128 pass phrase (ive also tried wep hex)>enter key>open system(ive tried shared key too)

It just says "wireless network connection to 2wire164 (0%) forever

                              OR
The window with "passphrase required by wireless network" keeps appearing, but when i enter it, it still comes up, and the internet doesnt work.

2) Manual configuration
  a) I enter network name (essid): 2wire164 
   b) password type: wep hex(so the tech guy at yahoo dsl told me)
   c) network password: ive entered it and im sure its correct
   d) configuration: i do auto config(DHCP)

---

### Post by renzokuken on 2008-04-15
do you know what make model your wireless card or what chipset it is based on? could you post the output of 

```
lsusb
```

---

### Post by swimm3r137@gmail.com on 2008-04-15
bus 003 device 001:id 0000:0000
bus 002 device 001:id 0000:0000
bus 001 device 003:id 045e:00el microsoft corp
bus 001 device 001:id 0000:0000

---

### Post by renzokuken on 2008-04-15
ok, that doesnt seem to reveal anything, can you try

```
lspci
```

---

### Post by swimm3r137@gmail.com on 2008-04-15
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11) 
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02) 
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) 
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller 
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller 
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller 
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

I'm still trying to stay with ubuntu =)  Patience really is the key hehe

---

### Post by renzokuken on 2008-04-15
what version of ubuntu are you using? sorry to keep asking one question at a time.

if you're using Feisty this thread might help [http://ubuntuforums.org/showthread.php?t=424994](http://ubuntuforums.org/showthread.php?t=424994) might not be relevant for gutsy though

---

### Post by swimm3r137@gmail.com on 2008-04-15
im using 7.10 (64bit aklternate)  Is that called feisty or gutsy?  Lol whats with ubuntu's update lingo?  K THANKS, i hope it works...  Otherwise, back to windows i go.  Sigh, theres always something that doesn't work...  Sucks tho, cuz I NEED the internet, otherwise, if it was something else, id just settle

---

### Post by swimm3r137@gmail.com on 2008-04-15
god damm it lol, im using gutsy.  I dont know what difference it makes, but regardless, when i attempted to look for bcm3xx-fwclutter, it can't be found.  Thats probably what you meant when you were asking about what version i was using.  So.......****...  I don't know what else to do, ugh!

---

### Post by cj13579 on 2008-04-15
Hey Guys

can I jump on ship here as I am in EXACTLY the same position. A recent convert from Vista I cant connect to any wireless networks. Like swimm3r I am also using Gutsy but using different hardware..

When I do the "lspci" command in the terminal i get...

chris@chris-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Many thanks in advance for your help/advice


Edit [1]: I am a complete newbie to this Ubuntu thing, however, i managed to do a scan for wireless networks in the area. I know that there is more than one available network as i am sitting next to another laptop which is connected to one and showing another. Yet in Ubuntu when i run the "iwlist scanning" command i get this output:

chris@chris-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

chris@chris-laptop:~$ 

Help would be greatly appreciated.

---

### Post by renzokuken on 2008-04-16
swimmer, the fwcutter package IS available in gutsy so i assume the same method as described for Feisty would work

copy and paste the following commands into your terminal

NOTE: you need to be connected to the internet for this so make sure you have a wired connection plugged in and working first

```
sudo apt-get update
```
```
sudo apt-get install bcm43xx-fwcutter
```

---

### Post by swimm3r137@gmail.com on 2008-04-16
Thankyou renzokuken.  I havn't tried this solution yet, only because in frustration, I HOPED that installing the 8.04 beta might be the solution.  Apparently I was wrong when I installed it over 7.10 and realized the same problem occured.  Question tho-  For the method you just posted, do you think it will work in the 8.04 beta, or the finished 8.04 version(when it comes out)???

---

### Post by swimm3r137@gmail.com on 2008-04-16
It works.  THANKYOU THANKYOU THANKYOU!!!!  I owe you everything.  Thankyou for this solution renzokuken, I appreciate it more than anything!  Oh, btw.... even thought it works, why is the percentage of the wireless connection SO MUCH LESS than windows??/  The range is much less...  It sits at like 48%.  Anyway to increase that?

---

### Post by renzokuken on 2008-04-17
> **swimm3r137@gmail.com said:**
> Thankyou renzokuken.  I havn't tried this solution yet, only because in frustration, I HOPED that installing the 8.04 beta might be the solution.  Apparently I was wrong when I installed it over 7.10 and realized the same problem occured.  Question tho-  For the method you just posted, do you think it will work in the 8.04 beta, or the finished 8.04 version(when it comes out)???

theres no reason why it shouldnt work for 8.04, although Hardy (8.04) has a much newer kernel into which many new/better wireless drivers were added.....so who knows, Hardy may support your wireless out of the box anyway

> **swimm3r137@gmail.com said:**
> It works. THANKYOU THANKYOU THANKYOU!!!! I owe you everything. Thankyou for this solution renzokuken, I appreciate it more than anything! Oh, btw.... even thought it works, why is the percentage of the wireless connection SO MUCH LESS than windows??/ The range is much less... It sits at like 48%. Anyway to increase that?

I'm glad it worked dude.......always nice to see people overcoming their issues.

As for the signal strength, i wouldnt read too much into the value it gives. Some drivers and wireless cards never display the correct signal strength in Linux. Unless your connection is significantly slower while browsing/downlaoding than it is on Windows, i'd just ignore it.

---

### Post by cj13579 on 2008-04-17
renzokuken,

do you think that this fwcutter thing would work for me? 

thanks

---

### Post by ryanhaigh on 2008-04-17
That information is for broadcom chipset wireless cards only and is not relevant to your issue becuase you have a **Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)** wireless card.

Search the forum for AR5006EG and that might give you some answers, here for example: [http://ubuntuforums.org/showthread.php?t=751901](http://ubuntuforums.org/showthread.php?t=751901)

---

