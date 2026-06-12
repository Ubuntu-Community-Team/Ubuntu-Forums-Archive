---
title: "How do we use wireless"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by smithky on 2008-11-03
can some body help me or direct me on how to check to see if my wireless is installed and if so how to connect it thanks in advanced my pc is a compaq c700 model c774tu

---

### Post by TenPlus1 on 2008-11-03
I went into the Network Connections option in Preferences and clicked on the Wireless tab and filled in the information to setup a wireless connection...  It detected the wireless card no probs but for some reason wouldn't let me use it (worked in Hardy)...

---

### Post by smithky on 2008-11-03
see i dont know what hardy is or any thing im new to ubuntu so yeah im a nub can any one help ?

---

### Post by jgaudario on 2008-11-03
yes, i'm  new to this also. a friend gave me ubuntu. 
I really need help on how to connect to the internet. i have wireless on my laptop, i have a windows xp os. the wireless works fine in xp but when i switch to ubuntu it doesnt work
i tried configuring it to wlan0,lo and everything else, it says that i may have type it incorrectly or my system doesn't have the interface:confused:what??? i have a intelwireless, do i need to load that driver on to ubuntu, or do i load a window wireless driver? pls help. thank you in advance.
jgaudario

---

### Post by AndyCee on 2008-11-03
**@smithky**
The wireless settings are, by default, in the area at the top-right corner of the screen (move the mouse over the icons to see what they are).

Click on it to see what networks your laptop can see without any configuration. If the network you want isn't detected, you'll have to go to "connect to other network" or "manually configure network" to enter details like password etc.

To check which version you are using, go to System -> About Ubuntu at the top left of the screen and it will hopefully be either Hardy Herron or Intrepid Ibex.

**@jgaudario**
Open a terminal (in Applications->Accessories->Terminal) and type
```
lspci | grep Network
```
in the same case as shown, to see what device is loaded/detected.

@Tenplus1
More info needed, sorry.

---

### Post by smithky on 2008-11-03
> **AndyCee said:**
> **@smithky**
The wireless settings are, by default, in the area at the top-right corner of the screen (move the mouse over the icons to see what they are).

Click on it to see what networks your laptop can see without any configuration. If the network you want isn't detected, you'll have to go to "connect to other network" or "manually configure network" to enter details like password etc.

To check which version you are using, go to System -> About Ubuntu at the top left of the screen and it will hopefully be either Hardy Herron or Intrepid Ibex.

**@jgaudario**
Open a terminal (in Applications->Accessories->Terminal) and type
```
lspci | grep Network
```
in the same case as shown, to see what device is loaded/detected.

@Tenplus1
More info needed, sorry.

i am using intripd and it has nothing to do with wireless when i click the network icon only wired ???

---

### Post by AndyCee on 2008-11-03
Ok. That means Ubuntu isn't detecting a working wireless card. Standard support questions - no offense intended if obvious.

1) Check wireless switch is on (either a physical switch or hold function key with F1 - F12 key marked with wireless icon [eg. Fn + F1 on my laptop]). Sometimes when switching between operating systems the soft-switch turns off/on - even if you've never used it before. I have heard many an experienced computer user at the point of breaking their computer before realising the little wireless light wasn't actually on.

2) Right-click on network icon and make sure "Enable wireless"is checked. They should be, but that would obviously prevent connection.

3) Follow the instructions I gave to jgaudario, to make sure your hardware is detected.

Also - are you using a liveCD or have you installed on the computer? If using a liveCD, there is a chance a driver needs to be installed to use the wireless card.

---

### Post by NE Key on 2008-11-03
> **smithky said:**
> see i dont know what hardy is or any thing im new to ubuntu so yeah im a nub can any one help ?

Hardy Heron is Ubuntu version 8.04 ( 8 for 2008 and 4 for April).

The latest version is Intrepid Ibex (8.10) of October this year.
(versions run alphabetically - the one before Hardy was Gutsy Gibbon-7.1)

The next point is has your computer detected the wireless card.

You will need to know how to enter commands directly, or code as some call it. You will have to open a "terminal" or command line window.

From the menu choose Applications>>Accessories>>Terminal

then type in; lspci

This commands Lists all your PCI cards and more. You should get a line that shows your wireless card. It will also tell you the details of the manufacturer and chip.
Use that info to search in this forum for the how to install.

(Too slow replying - others have beaten me to it with better answers !)

---

### Post by smithky on 2008-11-03
> **AndyCee said:**
> Ok. That means Ubuntu isn't detecting a working wireless card. Standard support questions - no offense intended if obvious.

1) Check wireless switch is on (either a physical switch or hold function key with F1 - F12 key marked with wireless icon [eg. Fn + F1 on my laptop]). Sometimes when switching between operating systems the soft-switch turns off/on - even if you've never used it before. I have heard many an experienced computer user at the point of breaking their computer before realising the little wireless light wasn't actually on.

2) Right-click on network icon and make sure "Enable wireless"is checked. They should be, but that would obviously prevent connection.

3) Follow the instructions I gave to jgaudario, to make sure your hardware is detected.

Also - are you using a liveCD or have you installed on the computer? If using a liveCD, there is a chance a driver needs to be installed to use the wireless card.

ok option 1 i push the button nothing happens 

2 the option enable wireless is not there 

3 nothing happens when i type it in the termanal

---

### Post by AndyCee on 2008-11-03
> Too slow replying - others have beaten me to it with better answers !
Moo ha ha.

Um, yeah, happens to me all the time :-) Good info though NE key.

---

### Post by NE Key on 2008-11-03
This may be a stupid question but do you have a wireless network ?
Is your router turned on ?

---

### Post by smithky on 2008-11-03
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

how do i install it or check that it is installed and how do i use it lol

---

### Post by AndyCee on 2008-11-03
Are you using a liveCD or have you installed on the computer?

While we're here, go to System>>Administration>>Hardware Drivers.

This will tell you if there's a proprietry driver to install. The wireless one may be there.

In terminal [again, sorry] try ```
ifconfig wlan0
```

Edit: You peoples are too fast ;)

---

### Post by AndyCee on 2008-11-03
> **smithky said:**
> 01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

how do i install it or check that it is installed and how do i use it lol

If it's there, the device is recognised by Ubuntu.

It may have a propriety driver, which will have to be downloaded. I'm not sure. [I can't look it up now - I'm studying for my final two exams :s ] See my previous post on how to check.

My opinion, as someone who currently configures wireless settings for uni students for a living, is that the software switch ["Fn" + "F1"-"F8"] is off. But I have to trust you've got it on, so that's all from me today, I'm afraid.

Good luck. I'll check back in 22 hours or so.

---

### Post by smithky on 2008-11-03
> **NE Key said:**
> This may be a stupid question but do you have a wireless network ?
Is your router turned on ?

i have 2 routers and yes there turned on how do i check to see if the drivers are installed?

---

### Post by smithky on 2008-11-03
> **AndyCee said:**
> Are you using a liveCD or have you installed on the computer?

While we're here, go to System>>Administration>>Hardware Drivers.

This will tell you if there's a proprietry driver to install. The wireless one may be there.

In terminal [again, sorry] try ```
ifconfig wlan0
```

Edit: You peoples are too fast ;)

when i type that in termanial it say device not found and ubuntu is installed on computer when i look in hardware drivers it has my wireless card there it say drivers are running any ideas???

---

### Post by smithky on 2008-11-03
what  is a proprietary driver???

---

### Post by smithky on 2008-11-03
anyone?

---

### Post by jgaudario on 2008-11-03
[QUOTE=AndyCee;6094468]**@smithky**
The wireless settings are, by default, in the area at the top-right corner of the screen (move the mouse over the icons to see what they are).

Click on it to see what networks your laptop can see without any configuration. If the network you want isn't detected, you'll have to go to "connect to other network" or "manually configure network" to enter details like password etc.

To check which version you are using, go to System -> About Ubuntu at the top left of the screen and it will hopefully be either Hardy Herron or Intrepid Ibex.

**@jgaudario**
Open a terminal (in Applications->Accessories->Terminal) and type
```
lspci | grep Network
```
in the same case as shown, to see what device is loaded/detected.

@Tenplus1
More info needed, sorry.[/QUOTE
yes the wireless settings are by default, till i started messing with it not knowing what i'm doing. but i'm not one to give up,
i think it's hardy herron.
thank you, it's a start.:p

---

### Post by smithky on 2008-11-04
> **jgaudario said:**
> [QUOTE=AndyCee;6094468]**@smithky**
The wireless settings are, by default, in the area at the top-right corner of the screen (move the mouse over the icons to see what they are).

Click on it to see what networks your laptop can see without any configuration. If the network you want isn't detected, you'll have to go to "connect to other network" or "manually configure network" to enter details like password etc.

To check which version you are using, go to System -> About Ubuntu at the top left of the screen and it will hopefully be either Hardy Herron or Intrepid Ibex.

**@jgaudario**
Open a terminal (in Applications->Accessories->Terminal) and type
```
lspci | grep Network
```
in the same case as shown, to see what device is loaded/detected.

@Tenplus1
More info needed, sorry.[/QUOTE
yes the wireless settings are by default, till i started messing with it not knowing what i'm doing. but i'm not one to give up,
i think it's hardy herron.
thank you, it's a start.:p

u said that all ready

---

### Post by AndyCee on 2008-11-04
**@Smithky:**That wasn't me, jgaudario just accidentally deleted a bracket in his quote :).

Proprietary drivers don't come bundled with Ubuntu. They are downloaded from the "Hardware Drivers" screen (if you enable it).

If on that screen down the bottom it says "This driver is enabled and currently in use", than the driver is installed and enabled. Otherwise you have to click the button to enable it.

I'm afraid I'm out of ideas for remote support. The only reason I can think why wireless won't work (it should automatically, by the way, this isn't supposed to happen) is a software switch.

If you get sick of waiting, type a new post saying "Bump". It's a polite way to draw attention to your question, but only do it once or twice a day.

Sorry, good luck. I'll check back when I have time.

---

### Post by smithky on 2008-11-04
It says that the driver is installed and running so that must mean that ubuntu is picking it up.

Could it be a compatibility issue ? or maybe a driver issue.

---

### Post by AndyCee on 2008-11-05
Well, I have some good news - and that is someone with the same card posted a solution here:

[http://ubuntuforums.org/showpost.php?p=6086847&postcount=2](http://ubuntuforums.org/showpost.php?p=6086847&postcount=2)

(and another here - same procedure)
[http://ubuntuforums.org/showpost.php?p=5711824&postcount=6](http://ubuntuforums.org/showpost.php?p=5711824&postcount=6)

It's very clear, however, it's not very user-friendly and requires alot of terminal work and a working wired Internet connection. While everything should be fine, I've never had to do it before.

Basically it involves installing a different driver, which has yet to become easy in the linux world :(

---

### Post by smithky on 2008-11-05
> **AndyCee said:**
> Well, I have some good news - and that is someone with the same card posted a solution here:

[http://ubuntuforums.org/showpost.php?p=6086847&postcount=2](http://ubuntuforums.org/showpost.php?p=6086847&postcount=2)

(and another here - same procedure)
[http://ubuntuforums.org/showpost.php?p=5711824&postcount=6](http://ubuntuforums.org/showpost.php?p=5711824&postcount=6)

It's very clear, however, it's not very user-friendly and requires alot of terminal work and a working wired Internet connection. While everything should be fine, I've never had to do it before.

Basically it involves installing a different driver, which has yet to become easy in the linux world :(

the site that hosts the file wont let me download the file and the site is up and working

---

### Post by AndyCee on 2008-11-07
I see what you mean.

The site has changed. For that line try:

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)

Or just go to [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) and download "madwifi-hal-0.10.5.6-current.tar.gz" to your home directory.

---

### Post by smithky on 2008-11-07
IT WORKS i done the 2nd idea and it worked i have wireless and its connected thank you so much :P

---

### Post by Riqz on 2008-11-07
> **smithky said:**
> IT WORKS i done the 2nd idea and it worked i have wireless and its connected thank you so much :P

Lucky you man... You think you had it hard? Try a Broadcom 4318 card ... I still not able to enter the airwaves with mine

---

### Post by AndyCee on 2008-11-09
Glad to help

:)

---

### Post by jgaudario on 2008-11-11
> **smithky said:**
> i am using intripd and it has nothing to do with wireless when i click the network icon only wired ???

i still don't have my wireless up. i do have hardy herron. anyway, i went to this link, LinuxTent(aboSamoor's post on apr.28, '08, btw, thanks, it got me this far) and so far this is what i got: in the terminal i typed, dmesg \ grep iw1, and this is the message it gave:
iw13945: radio frequency kill switch is on:
kill switch must be turned off for wireless networking to work.

i checked my wireless(pro/intel) and i can't find any kill switch. please help.
thanks.

---

### Post by jgaudario on 2008-11-19
hi guys,
this might be going back a bit. i search many of the wireless thread problems. still couldn't find any solution and i'm a bit confused, still a nub.
i really need help, this is costing me time and money. i go to the mall and connect to their wireless, on winxp it's fine.
i have a neo laptop m52n q-note, core duo, with intel pro/wireless 802.11abg, if any of you guys use neo, pls do jump in and help.
when i use ubuntu 8.04, my wireless wont connect. it says, along the lines, make sure you typed it correctly and your system supports interface.
i config it to wlan0:avahi, whatever that avahi means???
i tried lo, still no connection.
i tried these commands on the terminal, here are all the outputs:
joel@Neo:~$ [COLOR="Yellow"]lspci[/COLOR]
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:07.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
joel@Neo:~$[COLOR="Yellow"] lsusb[/COLOR]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
joel@Neo:~$ [COLOR="Yellow"]lshw -class network[/COLOR]
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:0b:5c:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:90:f5:67:35:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
joel@Neo:~$ 

so, what am i looking for, it seems to detect that i have a wireless interface, etc.
pls help.

---

