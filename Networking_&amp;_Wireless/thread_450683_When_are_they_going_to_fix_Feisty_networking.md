---
title: "When are they going to fix Feisty networking ?"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-05-21
So we've been running Fiesty for a month now and I've submitted a couple wireless networking bugs.  Still no fixes.  Specifically, I have the following problems.

a) I can't use KNetworkManager or networking doesn't work at all.

b) I have to do a sudo /etc/init.d/networking stop/ start every time I reboot my computers to get networking working.  This happens on 2 different machines !

c) The changes I make to System Settings -> Networking don't seem to stick.   And half the time when I use "Administrator Mode", it blocks me from making any changes at all !

So when can we expect a fix ?  Surely I'm not the only one having these issues !  I can't believe such major issues haven't been addressed.

Thanks.

---

### Post by Kobalt on 2007-05-21
When you see the number of wifi chipsets now available and the reluctance of some manufacturers to provide hardware information, you can understand it takes some time to have every hardware working out of the box in a free and open source OS.

---

### Post by daller on 2007-05-21
Feisty is the first version of Kubuntu to provide KNetworkManager by default!
It's come a great way since editing /etc/network/interfaces (which you can still do, if you are tired of KNM!)
Let's give this a release or two to mature!

---

### Post by RonnieRonnieRonnie on 2007-05-21
Same here.  I bought new hardware just before switching to Feisty, thinking this would be great.  Well, networking just ups and dies after a period of a few minutes to several hours - average of about 3-4 hours before suddenly conking out..  The LEDs on the ethernet port start flashing like it's tryiing to init the hardware.  There is no ping, nothing is reachable, /etc/init.d/netowrking restart does nothing, nfs drives disconnect, etc.  dmesg shows NETDEV Watchdog eth1 times out.  The only fix is to power down the machine - not even reboot - power down.  I have a Jetway Mobo with an NVIDIA chipset (NFORCE MCP51), running an AMD X2 SMP.  On-board Nvidia ethernet.  I tried putting in a PCI ethernet card (a Realtek) - it does exactly the same thing with or w/o the in-board NIC disabled.  Tried turning off ACPI at the BIOS - no effect.  

I see others reporting problems like this, but no solutions.  It is pretty fundamental.  Is there any way short of powering down to re-init the ethernet hardware?  That would at least provide a temporary fix.

---

### Post by kevdog on 2007-05-21
I don't want to hear crap about letting the Feisty version mature a week or two before complaining.  I was using Edgy and manually installed Knetworkmanager and everything worked great.  After upgrade to Feisty, had to resort to manual tweaking of interfaces file, and as the other user pointed out above have to restart the networking daemon after logging in to get networking working.  No change of hardware on my end occurred between Edgy and Feisty.

What I am complaining for?? The OS is free but I guess with upgrades you have to take a step backwards before moving forwards!

---

### Post by elmerfud on 2007-05-21
I came from Fedora.   At least with it you could massage the system to get things working automatically.  I haven't been able to with Fiesty.  Its a serious step backwards and keeps me from recommending it to others.  I can't believe it got released this way. 

And I don't think its specific to any one wireless driver.  I think the problem is knetworkmanager.

---

### Post by Pyrogenesis on 2007-05-22
Seeing as Feisty has serious problems with the RT2xxx cards for which *the company itself provides free open source linux drivers*, I think something's been messed up with this release in this respect. :(

---

### Post by bait on 2007-05-22
> **Pyrogenesis said:**
> Seeing as Feisty has serious problems with the RT2xxx cards for which *the company itself provides free open source linux drivers*, I think something's been messed up with this release in this respect. :(

 The company released the source code not the drivers, the drivers are developed by a community group.

From the linux page at 

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

> Ralink is very active in the Linux community, and provides source code for many of its client drivers to developers. You can find our Linux drivers and supporting information below:

The group doing the development for the drivers are at the following link.

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

---

### Post by SittingCrow on 2007-05-22
Try my solution get back to edgy and put a smile on your face.

---

### Post by hoodwink on 2007-05-22
My brief answer to your question: probably never. They're already working on Gutsy, and fixes for Feisty are few and far between. Network Manager works like a champ for a few selected chipsets, but it's a major regression for most.

I have a Thinkpad wth Atheros wireless. It works only with an unsecured connection, fails miserably with WEP. The current kernel for Feisty appears to have worsened the situation. Using the current kernel (2.6.20-15-generic), I get absolutely no attempt to connect with a WEP passphrase proteted site. With an older kernel (-9) the unit connects but will not obtain a DHCP lease. Another user (no idea abut the chipset) using Dapper was able to connect with no problems, but then he is using Wireless Assistant.

I have a friend with a Broadcom chipset, and he had to remove Network Manager ad revert to using Wireless Assistant. During the Feisty Beta, there were many and bitter complaints about Network Manager, but the complaints fell on deaf ears. It was too important to release on time, even though many users were screwed over.

The worst thing about Network Manager is that there is absolutely no debugging information to give you a clue about what is wrong.

---

### Post by RonnieRonnieRonnie on 2007-05-22
I turned down the clock speed on my machine (see my post above) and it seemed to help.  I was running an AMD X2 rated at 1.9 Ghz at 2.13 Ghz.  I am running it now at 1.8 GHz and so far so good.  Goal now is to getg 24 hrs uptime.  Given that my Debian machine typically gets hundreds of DAYS of uptime before I decide to reboot it for some reason, this is pretty pathetic still.  Time will tell.

---

