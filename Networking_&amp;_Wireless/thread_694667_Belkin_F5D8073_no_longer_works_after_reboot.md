---
title: "Belkin F5D8073 no longer works after reboot?"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by nine7six on 2008-02-12
I followed these steps:
> **darrelltwo said:**
> THIS CARD WORKS!!!!! YAY! Right out of the box on Gutsy. I popped it in, put the CD in, copied the XP driver folder to my hard drive, then used the GUI NDISWRAPPER to load the driver. It could not have been easier! (well, I guess plug-n-play would have been easier)

Exact steps.
1) Put Card in computer.
2) Put CD in drive
3) Browse to XP Driver, and copy driver folder with all contents to your hard drive.
4) Go to ADD/Remove Programs and search for NDISWRAPPER
5) Load the WINDOWS WIRELESS DRIVERS Tool.
6) Go To SYSTEM, ADMINISTRATION, WINDOWS WIRELESS DRIVERS
7)Click on Install New Driver
8) Browse to XP folder and load *.INF file
9) You should then see the driver loaded and hardware present in the window.
10) Click Configure Network
11) Setup your wireless network info.
12) After all of that, you need to make sure you hit the checkbox that enables the wireless network.

You will not be able to configure the card from the network drop-down next to the TIME/DATE section of your tool bar. You will have to use the Windows Wireless Drivers tool for that. 

Hope this helps some of you newer guys, since this is way easier than compiling, sorting, and waving dead chickens over your head.

Darrelltwo?

Source: [http://ubuntuforums.org/newreply.php?do=newreply&p=3892042](http://ubuntuforums.org/newreply.php?do=newreply&p=3892042)

Any my wireless worked great all night long. I turned my laptop off before I put it in my bag this morning to go to work and then when I booted it back up at work my wireless no longer works? It can see my network and several around me, but cannot connect to any of them? Anything I can look into? Thanks for any help.

-Mike

---

### Post by dca on 2008-02-12
At CLI, type:  sudo modprobe -i ndiswrapper
 
then restart laptop and see if works...

---

### Post by nine7six on 2008-02-12
> **dca said:**
> At CLI, type:  sudo modprobe -i ndiswrapper
 
then restart laptop and see if works...

Still does not work. It goes through the motions but never connects.

---

### Post by dca on 2008-02-12
What chipset does that use???  Are you sure it's not the BCM43xx series?  It sounds to me like another driver is loading on start-up along with the one you changed to...  When you installed Ubuntu did it harass you about 'restricted drivers' and which ones were in use?

---

### Post by nine7six on 2008-02-12
> **dca said:**
> What chipset does that use???  Are you sure it's not the BCM43xx series?  It sounds to me like another driver is loading on start-up along with the one you changed to...  When you installed Ubuntu did it harass you about 'restricted drivers' and which ones were in use?

It's a Belkin N Wireless ExpressCard model # F5D8073. 
I did not have it in when I installed Ubuntu. The driver does not show up under 'Restricted Drivers'. Is there a way to see what other drivers my system may be trying to associate with this card? Thanks for your help.

---

### Post by nine7six on 2008-02-12
Any sys info I could post that may help in figuring out what the issue is?

---

### Post by dca on 2008-02-12
...wait, is this the first time you've tried using it at work?  You can see the Access Points in Network Manager at work currently?

---

### Post by nine7six on 2008-02-12
> **dca said:**
> ...wait, is this the first time you've tried using it at work?  You can see the Access Points in Network Manager at work currently?

yes, this is the first time. Yes, I can see all of the networks at work (and several close by) along with their strength. When I double-click on one of the networks it say's it's trying to connect but it does not. I've tried my work networks along with some of the open networks in the area but it has not been able to connect to any of them.

---

### Post by dca on 2008-02-12
You'll have to forgive me, generally if you can see it in the network manager your driver is working...  Is there anything stored in your 'System -> Administration -> Network' settings.  I believe both wired & wireless should have roaming mode enabled and set to obtain IP from DHCP.  Also there shouldn't be anything in your DNS tab settings if you're not connected to anything.  Then restart your system and try connecting again.  The only times I've seen people not get an IP (this far in the game) is if they're not actually connecting to an Access Point/Wireless Router (like wireless card from another system) or the security used on the AP is something that confuses network manager.
 
For instance:  my laptop works fine on all connections, security WEP, WPA, etc.  Every combination, you name it...  I built an Ubuntu system for a family member, it contained a Dynex (bcm43xx) wireless card, real cheap, from Best Buy.  It can't connect to any APs that use WEP w/ Hex key.  It can only access the router w/ it set to WEP @ 64bit ASCII on the first key (not two, three, four)...  Yet my laptop accesses the thing fine.  Go figure...

---

### Post by nine7six on 2008-02-12
> **dca said:**
> You'll have to forgive me, generally if you can see it in the network manager your driver is working...  Is there anything stored in your 'System -> Administration -> Network' settings.  I believe both wired & wireless should have roaming mode enabled and set to obtain IP from DHCP.  Also there shouldn't be anything in your DNS tab settings if you're not connected to anything.  Then restart your system and try connecting again.  The only times I've seen people not get an IP (this far in the game) is if they're not actually connecting to an Access Point/Wireless Router (like wireless card from another system) or the security used on the AP is something that confuses network manager.
 
For instance:  my laptop works fine on all connections, security WEP, WPA, etc.  Every combination, you name it...  I built an Ubuntu system for a family member, it contained a Dynex (bcm43xx) wireless card, real cheap, from Best Buy.  It can't connect to any APs that use WEP w/ Hex key.  It can only access the router w/ it set to WEP @ 64bit ASCII on the first key (not two, three, four)...  Yet my laptop accesses the thing fine.  Go figure...

Not sure.. I'm at home now and it talks to my router fine (belkin n router). I was trying to connect to networks around my work that had no security enabled and it would not connect then either? strange. I'll just continue to use a wired connection at work until I can get it figured out.. Thanks for your assistance.

---

