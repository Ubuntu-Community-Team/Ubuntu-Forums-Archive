---
title: "Installing Hardware Drivers from Flash Drive?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by neu5eeCh on 2009-12-31
On a more serious note:  I burned the Ubuntu Netbook Remix to a flash drive and tried it out on my wife's HP Netbook (ran it off the flash drive rather than install).  (If I muck up my wife's netbook, my life is forfeit.)  So... I want to make sure Ubuntu works as flawlessly on her machine as on my other two laptops. However, I can't seem to install the proprietary hardware drivers needed to activate the wireless. Is this a problem with a "live CD"? Whenever I try to activate the broadcom drivers, Ubuntu appears to "download" and install the driver. Then asks me to restart.  After I've restarted, the "Hardware Drivers" application tells me that the driver is installed but not in use?  End result? I can't use the wireless.   What's up? Will the wireless driver install and work on a "live flash drive"?

---

### Post by tom.swartz07 on 2009-12-31
> **VTPoet said:**
> On a more serious note:  I burned the Ubuntu Netbook Remix to a flash drive and tried it out on my wife's HP Netbook (ran it off the flash drive rather than install).  (If I muck up my wife's netbook, my life is forfeit.)  So... I want to make sure Ubuntu works as flawlessly on her machine as on my other two laptops. However, I can't seem to install the proprietary hardware drivers needed to activate the wireless. Is this a problem with a "live CD"? Whenever I try to activate the broadcom drivers, Ubuntu appears to "download" and install the driver. Then asks me to restart.  After I've restarted, the "Hardware Drivers" application tells me that the driver is installed but not in use?  End result? I can't use the wireless.   What's up? Will the wireless driver install and work on a "live flash drive"?

When using it in Live, you could technically download it and run it from there.

The many times that I run my Ubuntu in live mode, I end up doing the same. 

Just install the drivers and try to connect.



The only other option would be to change the liveUSB to a 'persistent' mode, where it saves the changes that you make, allowing you to install the driver and reboot the system that way. Head to [www.pendrivelinux.com](www.pendrivelinux.com) for some guides on how to do that there.

---

### Post by neu5eeCh on 2009-12-31
> **tom.swartz07 said:**
> When using it in Live, you could technically download it and run it from there.

The many times that I run my Ubuntu in live mode, I end up doing the same. 

Just install the drivers and try to connect.



The only other option would be to change the liveUSB to a 'persistent' mode, where it saves the changes that you make, allowing you to install the driver and reboot the system that way. Head to [www.pendrivelinux.com]("http://www.pendrivelinux.com") for some guides on how to do that there.

If you mean download it from the net... I can't. There's no Ethernet port on the Netbook and I don't own a USB to Ethernet adapter. That said, Ubuntu appears to download the driver from the flash drive - but doesn't seem to activate it? 

Or if it does, it states that the driver is *not in use* (and I don't know how to change that - that is, put it ***in use)***. As to persistent mode - I left almost 1G available for just this circumstance. (Or at least I thought I did.) 

But persistent mode seems to be working.  After I installed the broadcom driver and rebooted, Ubuntu recognized the hardware driver as being installed, but **not in use**?

---

### Post by tom.swartz07 on 2009-12-31
> **VTPoet said:**
> If you mean download it from the net... I can't. There's no Ethernet port on the Netbook and I don't own a USB to Ethernet adapter. That said, Ubuntu appears to download the driver from the flash drive - but doesn't seem to activate it? 

Or if it does, it states that the driver is *not in use* (and I don't know how to change that - that is, put it ***in use)***. As to persistent mode - I left almost 1G available for just this circumstance. (Or at least I thought I did.) 

But persistent mode seems to be working.  After I installed the broadcom driver and rebooted, Ubuntu recognized the hardware driver as being installed, but **not in use**?

after you activate it, does the wireless internet icon appear on the top panel?

the LiveUSB/LiveCD carries copies of all of the drivers that you should need, and installs it from there. 

Look and see if it allows you to connect- if it says you installed it, it should be there.

---

### Post by neu5eeCh on 2009-12-31
//after you activate it, does the wireless internet icon appear on the top panel?//

No. The icon remains inactive. I seem unable to activate the driver using the "Hardware Drivers" app, though the app claims to have downloaded and installed the driver.

I have a friend here who is somewhat more familiar with Linux (Fedora). Entering the following command: dmesg | grep -i broadcom (The Netbook uses broadcom...)

Results in the following:

[73.703399] b43-phy0: **[COLOR=Red]Broadcom[/COLOR]** 4312 WLAN found (core revision 15)
[73.756582] **[COLOR=Red]Broadcom [/COLOR]**43xx driver loaded [Features: PL Firmware-ID: FW13]

Instead of using Ubuntu Remix, I'm using Ubuntu on a liveUSB - with a Persistent folder. Wanted to see if using straight Ubuntu would make a difference.

(*Also, this morning, when I tried to reboot with the Remix, I lost keyboard and mouse functionality. The keyboard only functioned when I opened a shutdown window (by pressing the power key). Weird stuff...*)

Update: Also ran the lspci -vnn | grep 14e4

01:00.0 Network Controller [0280]: Broadcom Corporation BCM4312 802.11b/g [[COLOR=Red]**14e4**[/COLOR]:4315] (rev 01)

Lastly, noticed that [others have gotten this machine running ]("http://migsvuitton.com/blog/2009/05/more-on-ubuntu-and-hp-mini-1030nr/")successfully? Maybe this is only an issue with LiveUSB? I don't get it.

---

