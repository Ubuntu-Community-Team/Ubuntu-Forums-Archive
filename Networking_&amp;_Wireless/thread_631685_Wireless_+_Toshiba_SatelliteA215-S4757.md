---
title: "Wireless + Toshiba SatelliteA215-S4757"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by erik_gil on 2007-12-04
Can someone help me get my wireless running on Ubuntu(Gusty) for the love of g-d. After reading a couple of forums I thought i'll go ahead and give a detailed summary of my laptop. I'm using a fresh install of Gusty. This is the only problem im running into with Ubuntu. I don't want to go back to Windows, Please help if you can. Oh just thought i'll say this. My card is intigrated.

lspci | grep -i net
```

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

sudo lshw -C net
```
 
*-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1b:b5:7c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.4 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1B:38:1B:B5:7C  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe1b:b57c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5013395 (4.7 MB)  TX bytes:553567 (540.5 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Ok that should be sufficient information to know whats up with my ****. If you need any more info just let me know. Oh by the way, my Atheros driver is enabled under, Restricted Drivers Manager.

---

### Post by rustybronco on 2007-12-04
> **erik_gil said:**
> 
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       

.that and a search should get you started, network UNCLAMED (no driver) and the chipset AR5006EG.
such as   [http://madwifi.org/wiki](http://madwifi.org/wiki)   and [http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG)

and   [http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

you could do the madwifi install or possibly with ndiswrapper (how to also in the above link) and the proper windows driver.

---

### Post by erik_gil on 2007-12-04
Newbie to linux. Could you please tell me what to do to fix this problem? Like a detailed process please. Sorry for the bother but I dont want to mess up Ubuntu. For example. could you like possibly link me a site to get the drivers and a how to for ndiswrapper or madwifi, thanks

---

### Post by rustybronco on 2007-12-05
> **erik_gil said:**
> Could you please tell me what to do to fix this problem? Like a detailed process please.read the above links it's there.
 > Sorry for the bother but I dont want to mess up Ubuntu.it never is a bother, glad to help. do you to know how many times I have messed up my install?, lots.
 > For example. could you like possibly link me a site to get the drivers and a how to for ndiswrapper or madwifi, thanksexcept for the window drivers, I did. I'll be watching this post, just ask. 
The terminal is located in   applications>accessories>terminal, then right click > add launcher to panel

highlight the text/code you need,  cut is ctrl+c   and paste is   ctrl+shift+v (in the terminal)

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If it were me i'd use the madwifi install.
Dale

---

### Post by erik_gil on 2007-12-05
Cool man thanks for taking interest in my post, I really do appreciate it. This is what i've done so far. I ran into a problem on step two.

1. sudo gedit /etc/default/linux-restricted-modules-common
DISABLED_MODULES="ath_hal"

2. I typediit as root
ifconfig ath0 down
ifconfig wifi0 down
#Repeat these 2 ifconfig lines for every MadWifi device you have

gave me an error

```

ath0: ERROR while getting interface flags: No such device
wifi0: ERROR while getting interface flags: No such device

```

Is that a normal?

---

### Post by pandron on 2007-12-05
```

ath0: ERROR while getting interface flags: No such device
wifi0: ERROR while getting interface flags: No such device

```

I have the same problem, same wireless card, similar computer (A215-S4807).  When I click on the network-manager there is no wireless anything listed.

when I type *iwconfig *I get:
lo               No wireless extensions.
eth0          No wireless extensions.

I thing we are missing the "ath0" which would be the Atheros wireless card.

I also tried MadWifi which seemed to install smoothly from synaptic-package-manager, but made no difference.
I also tried installing ndiswrapper using both the XP version of net5211.inf and the Vista version called athr.inf (I think).  Anyway, niether made any difference.  I still get the same output with iwconfig

I also get exactly the same results as eric_gil with *sudo lshw -C net*. I notice that unter the Ethernet device we have a line:

logical name: eth0

But under the UNCLAIMED device there is no "logical name:ath0" (I assume there should be)

If anyone can help, thanks in advance!

----------------------------
Gutsy 32-bit, Satellite A215-4807, Atheros AR5007EG wireless card,

---

### Post by rustybronco on 2007-12-05
> **erik_gil said:**
> 
gave me an error

```

ath0: ERROR while getting interface flags: No such device
wifi0: ERROR while getting interface flags: No such device

```

Is that a normal?I have never done the madwifi install before, but as I see it yes, because you have no drivers in use.  
```

ath0: ERROR while getting interface flags: "No such device"
wifi0: ERROR while getting interface flags: "No such device"

```
I have not walked this road before, you and I will learn, but I will give you 100%

---

### Post by rustybronco on 2007-12-06
You might take a look a ndiswrapper install, this guy said he got it to work with  the AR5006EG chipset.  [http://ubuntuforums.org/showthread.php?p=3901936#post3901936](http://ubuntuforums.org/showthread.php?p=3901936#post3901936)

---

### Post by kevdog on 2007-12-06
Although the AR5006EG chipset should theoretically work with madwifi -- I know with this particular chipset there are many errors using madwifi when using the madwifi drivers contained within the linux-restriced package.  Perhaps compiling the madwifi sources from svn may solve the problem (I haven't seen any feedback proving or disproving this suggestion).  Others have used ndiswrapper along with the windows XP driver to get this card to work.  I'm willing to help you with either method.   As a new user the safest bet is probably ndiswrapper, however Im always curious to find out if other methods work and find solutions to non-working problems!

---

### Post by erik_gil on 2007-12-06
ok, i found the driver from [http://atheros.cz]("http://atheros.cz"), so Im going to go ahead and try to install it with ndiswrapper. Is there a post or anyway you could possibly guide me through the installation? That would be much appreciated. Thank you for your interested in helping me out.

---

### Post by rustybronco on 2007-12-06
See Kevdogs signature, ndiswrapper with...

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by erik_gil on 2007-12-06
ok after this command

ndiswrapper -l 

I get
[CODE
]net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
[/CODE]

what do i do to fix it?

---

### Post by rustybronco on 2007-12-06
> **erik_gil said:**
> ok after this command

ndiswrapper -l 

I get
[CODE
]net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
[/CODE]

what do i do to fix it?
click on the network icon, choose a network and add the info that it asks for (type of encription, passphrase or hex code ect...), then try to connect.

---

### Post by erik_gil on 2007-12-06
I might need to disable or blacklist the other driver because i still get
lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1b:b5:7c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

---

### Post by rustybronco on 2007-12-06
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

> Make sure no errors are reported **and you get something like**:
Quote:
bcmwl5: driver installed
device (14E4:4320) present  which you have

Then...
> Ok, to insert the ndiswrapper module into the linux kernel:

```
sudo depmod -a
```

did you get this far?

---

### Post by erik_gil on 2007-12-07
Yes I did. But dont I need to like blacklist the the Atheros Hardware HAL in order for ndiswrapper to work? If I do, whats the command for it?

---

### Post by rustybronco on 2007-12-07
sudo gedit /etc/modprobe.d/blacklist
blacklist (your driver needed to blacklist) i.e blacklist ath_pci
try it, you can always un-do it.
but you have no logical name or driver listed (unclaimed) again.
*** so no driver is loaded***

post the output of lsmod | grep ndis

---

### Post by rustybronco on 2007-12-07
You may want to go over the steps again.

---

### Post by pandron on 2007-12-07
I just thought I'd chime in again.  I am following this thread very closely.

I installed ndiswrapper (using synaptic), blacklisted ath_pci, restarted, and still have exactly the same problem that eric_gil is getting.  

My install of ndiswrapper *appeared* to go smoothly, however I still do not have the option "wireless network" under the network manager.  Just "Wired network" and "Manual Configuration".

Also my device is still "UNCLAIMED"

Then I tried Kevdogs ndiswrapper solution.  Everything went fine until I typed:

sudo modprobe ndiswrapper

At which point it said something like "module not present".  So maybe the install didn't go as well as I originally thought even though it showed no errors, AND when I type 

sudo ndiswrapper -l

I get:

net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)

Maybe it's time to start over... I'd like to have something new to try though before I do so.

Is it possible to manually assign the device to ath0?  Just a newbie thought...

--------------------------
Satellite A215-4807, Gutsy 32 Bit, AR5007EG Wireless

---

### Post by rustybronco on 2007-12-07
Just to let you know I haven't forgotten, I have been busy at work.

---

### Post by rustybronco on 2007-12-07
Back...

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,424/catid,2/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,424/catid,2/)

> Re:atheros device **168c:001c** does not load 2007/07/30 22:27 Karma: 0    
OK, Giri, thanks (as ever). 

Rebooting with ath_pci and ath_hal blacklisted and the XP driver from

[http://www.atheros.cz/download.php?atheros=AR5008&system=1](http://www.atheros.cz/download.php?atheros=AR5008&system=1)

made the card works. 

Thanks. Time to contribute to this project...
[http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_fireboard&Itemid=34&func=view&id=802&catid=2#802](http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_fireboard&Itemid=34&func=view&id=802&catid=2#802)


> Re:driver and wrapper show installed no life at al 2007/10/28 23:13 Karma: 0    
Yes, probably yes. Try to add:

blacklist ath_pci
blacklist ath_hal

to /etc/modprobe.d/blacklist and reboot. My wifi works with the drivers from
[http://www.atheros.cz/](http://www.atheros.cz/)

Hope this helps,

Post edited by: rmano, at: 2007/10/28 23:13 
> **erik_gil said:**
>  I also tried **MadWifi** which seemed to install smoothly from synaptic-package-manager, but made no difference
[QUOTE=DANGERTOOLS]Admin  
 Re:driver and wrapper show installed no life at al 2007/10/25 03:45 Karma: 2    
**Are you sure, that you don't use madwifi (that's the alternate driver mentionend)?** Check the wiki on how to handle that.[/QUOTE] Maybe that's why...

---

### Post by rustybronco on 2007-12-07
pandron, did you try to get your wireless working with the restricted drivers first before your  ndiswrapper install? if so I would un-check atheros hal, then blacklist both ath_pci and ath_hal and reboot to see if it works.

---

### Post by pandron on 2007-12-07
Ok, I blacklisted the ath_hal as well, and uncheck the HAL in the restricted drivers module (it was already labeled as "not used"), but now it's unchecked as well.

Then I downloaded the XP32 drivers from [www.atheros.cz](www.atheros.cz)

I unloaded the old net5211 and reloaded the new net5211 (probably a waste of time but...)

Then I added this line to blacklist:

blacklist ath_hal
(blacklist ath_pci was already there)


I also tried to type (just for kicks)
sudo modprobe ndiswrapper
and got:
FATAL:  Module ndiswrapper not found (or something like that)

I rebooted anyway, but of course, no change... :confused:

I really appreciate the help!  Please don't give up on us!  Do you think it's time for a fresh install?  Or is this salvagable?

---

### Post by rustybronco on 2007-12-07
> **pandron said:**
> 
I also tried to type (just for kicks)
sudo modprobe ndiswrapper
and got:
FATAL:  Module ndiswrapper not found (or something like that) because it can't find the file to insert into the kernel.
> I rebooted anyway, but of course, no change... :confused:
I really appreciate the help!  Please don't give up on us!  Do you think it's time for a fresh install?  Or is this salvagable?I think it's salvagable if it were me i would double check/re-do the ndiswrapper install making sure all the directories and inf. files are in the proper place, then depmod -a, modprobe ect.
ndiswrapper install  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
i wish I had that chipset it would be easier with it in front of me, but no matter, it is what it is.

I have one request, don't give up on me, i'm learning also.
I will see this through until it works, or I go down in flames (just kidding).

---

### Post by rustybronco on 2007-12-07
pandron, you know this post is about a AR5006EG chipset, I see in your signature you have a AR5007EG make sure the drivers are the same, if not get them.

---

### Post by pandron on 2007-12-07
WIRELESS IS WORKING!!!!!!  I'M POSTING THIS FROM UBUNTU!!!!

Ok, here's what I did:

Step 1:  I went into Synaptic-Package-Manager and marked MadWifi for removal.
Step 2:  Marked all three ndiswrapper packages for removal (the three that show up when I type "ndiswrapper" in the search box.
                1. ndisgtk
                2. ndiswrapper-common
                3. ndiswrapper-utils-1.9
Step 3:  Downloaded the latest ndiswrapper from sourcefoge.net (version 1.50)
Step 4:  Extracted the ndiswrapper to a folder called ndiswrapper-1.50 on the desktop
Step 5:  Open a terminal and typed "cd Desktop/ndiswrapper-1.50"  (i.e. go into the folder)
Step 6:  sudo make  (no errors)
Step 7:  sudo make install
Step 8:  sudo ndiswrapper -l   (get the name of any drivers that are installed: net5211 in my case)
Step 9:  sudo ndiswrapper -r net5211
Step 10: Then I downloaded the latest Windows XP-32 driver from [http://atheros.cz](http://atheros.cz)
Step 11: Extract the XP driver to a folder called Atheros on the Desktop.
Step 12: Open a terminal and go into the Atheros folder (cd Desktop/Atheros)
Step 13: sudo ndiswrapper -i net5211.inf
Step 14: ndiswrapper -l
        The output of that looks like this:

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

Step 15: iwconfig
       The ouput of that looks like this:


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WirelessNetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:11:5F:BB:C1   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Step 16:  reboot
Step 17:  click on the network icon and click on "manual configuration".  Wireless should now be one of the options...

Thanks for all the help!  This is very cool!

---

### Post by rustybronco on 2007-12-07
>  Toshiba Satellite A215-4807, AMD Turion64 X2, 2 Gb RAM, Graphics: ATI Radeon Mobility X1200, Wireless: Atheros AR5007EG(not yet working), Gutsy Gibbon 32-Bit
Reply With Quote time to change your signature....   congrats! and welcome.

---

### Post by Jeztastic on 2008-01-13
Hey, muchos gracios!

FINALLY got my wireless working!

You are a star!

---

### Post by wilk3sy on 2008-04-04
Hey guys, 

decided i want to migrate to linux. 

installed ubuntu 7.10 aka gutsy gibbon i believe.

Ive got the A215-S4757, with the same atheros wireless card. 

now ive tried many tutorials online, and i cant even get simple things like madwifi installed... i just dont understand why its not working for me.

Nevermind, hopefully you guys can sort me out.

Please let me know if there is anymore information you need.

Thanks

~wilk3sy

---

### Post by raiwo on 2008-04-04
> **wilk3sy said:**
> Hey guys, 

Nevermind, hopefully you guys can sort me out.

~wilk3sy

[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877) this should work

---

