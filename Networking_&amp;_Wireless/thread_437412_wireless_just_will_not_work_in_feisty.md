---
title: "wireless just will not work in feisty"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by tekdata on 2007-05-08
Hi guys,

Now, I'm by far no Linux newbie - I've been on board since Slakware 3.0, but I'm beat with this. I got a new Dell laptop with bcm43xx. Installed ndiswrapper, win32 drivers, etc. Got the card working. I can see networks. I have some success connecting to unencrypted networks, but just can't connected to WEP or WAP.

Tried nm-gnome, knm, wicd, etc, etc. Tried using the native bcm43xx driver with firmware, got it working, can't connect to WAP. Tried using a USB wifi adapter. Zytek or something. Got it working. Can't connect to WAP. Tried empty interfaces files, tried defined ones, tried WAP settings in interfaces file, etc, etc. Can't get it working.

Tried the same USB wifi adapter on my desktop after updatng to feisty fawn - exact same symptoms.

Help. Just help. I've wasted two nights on this. Is Feisty having issues with WAP in general? If yes, is somebody using an Inspiron with the dell expresscard bcm43xx successfully on ANY distro? If so, please let me know. I can't afford the time to mess with this. I need to work, so I'm on tethered-network right now.

---

### Post by stchman on 2007-05-08
> **tekdata said:**
> Hi guys,

Now, I'm by far no Linux newbie - I've been on board since Slakware 3.0, but I'm beat with this. I got a new Dell laptop with bcm43xx. Installed ndiswrapper, win32 drivers, etc. Got the card working. I can see networks. I have some success connecting to unencrypted networks, but just can't connected to WEP or WAP.

Tried nm-gnome, knm, wicd, etc, etc. Tried using the native bcm43xx driver with firmware, got it working, can't connect to WAP. Tried using a USB wifi adapter. Zytek or something. Got it working. Can't connect to WAP. Tried empty interfaces files, tried defined ones, tried WAP settings in interfaces file, etc, etc. Can't get it working.

Tried the same USB wifi adapter on my desktop after updatng to feisty fawn - exact same symptoms.

Help. Just help. I've wasted two nights on this. Is Feisty having issues with WAP in general? If yes, is somebody using an Inspiron with the dell expresscard bcm43xx successfully on ANY distro? If so, please let me know. I can't afford the time to mess with this. I need to work, so I'm on tethered-network right now.

Follow my procedure to get Broadcom 43xx cards working in Ubuntu.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

Follow the second section as it installs ndiswrapper for you.  I recommend you uninstall ndiswrapper before using this procedure.  It contains scripts and has .inf Widows drivers all there.

I have not tried this procedure with Feisty but it should work as well.

If you already have the card working then do this.

You will then need to install the wpasupplicant as this will support WEP, WPA and WPA2.

Follow this procedure for Gnome Network-Manager

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Just the bottom section about WEP, WPA and WPA2.

---

### Post by tekdata on 2007-05-08
I already have all those packages installed, and tried all those configuration sets.

I already can browse available networks. I have WPA supplicant. I can connect unencrypted. I can also attempted WPA connections, and supplicant will associate with my card, but will not associate with my router. I've also tried two different network cards. The 2nd card also works great in Breezy - just not in Feisty.

---

### Post by tekdata on 2007-05-08
After a clean reinstall, I managed to get the USB (Zylink, Zytek, or something) adapter to work with full WPA support.

However, the Broadcom adapter that came with the Dell is still screwed, both with ndiswrapper and the native driver (yes, I did the firmware thing). It seems to work with other distros, though.

My guess is it's just screwed in Feisty.

Any thoughts? If this USB stick keeps protruding, I will, eventually, break it off by accident.

---

### Post by Jouke74 on 2007-05-09
It is some error with passing through the WEP + WPA parameters from gnome-network-manager to the WPA supplicant while using certain (Ndiswrapper) drivers (Broadcom / Marvell ea). I tried everything as well, using the both network-manager and wifi radar. WPA + WEP fail, while cards & wireless networks are detected perfectly. Unprotected networks are connected ok.

STEP1:
- I needed to download the latest Ndiswrapper from the site (not the one coming with Ubuntu).
- I compiled it with make and installed it according to the site manual.
- Checked of course the network card was present.

STEP2:
- Use Windows XP to update (actually downgrade) my router to use WEP HEX instead of WPA!!!
- Limited my router to accept only me and my wife's MAC address (as extra security = not required).
- Made sure router assigns (static) address with DHCP.

STEP3:
- I deinstalled the network-manager and gnome-network-manager.
- I added the network monitor to the panel (to see if i have connectivity).
- I went to administration > networking (this one does not support WPA as far as I know, only WEP).
- Disabled the roaming mode.
- Entered manual configuration for the wireless card.
- Select right network with ESSID, WEP HEX, KEY and DHCP 
- Reboot, and there was my connection using WEP.

It's the only way i got it running.

---

### Post by glendavee on 2007-05-09
I had all sorts of problems getting my Airgo rt73 USB  card to work in Feisty after upgrading from Edgy. iwconfig and ndiswrapper -l both showed driver present and ok. uninstalling Network Manager and switching to Wicd didn't help.
Eventually I discovered that if USB card is unplugged at startup, then plugged in once system is up and running, Wicd finds it and everything works ok. Only drawback is that I have to do this everytime I boot.

---

### Post by tekdata on 2007-05-09
I'm discovering the same thing. My USB wifi only works if it's not present at bootup.

My expresscard wifi has now stopped detecting networks entirely. It's getting a little nuts. I'm wondering how SuSE's wifi support is looking.

---

### Post by tekdata on 2007-05-09
I should note in all this, I'm running a dual-core Turion 64 with 64-bit Ubuntu.

---

