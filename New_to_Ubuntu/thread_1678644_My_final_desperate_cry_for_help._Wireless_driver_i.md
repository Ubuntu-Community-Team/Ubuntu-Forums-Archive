---
title: "My final desperate cry for help. Wireless driver is installed, but hardware not found"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by pencils42 on 2011-01-30
If you want the long story:

[http://ubuntuforums.org/showthread.php?t=1673668&highlight=pencils42](http://ubuntuforums.org/showthread.php?t=1673668&highlight=pencils42)

We concluded that to get Windows back I'd need to buy a recovery disk. But I want to ensure I can't get ubuntu to work first.

If you want the short story, I deleted Windows. Ubuntu won't recognize any wifi network. I'm screwed.

I asked the woman across the street from me, who is a computer consultant, for help. She was able to download and install the correct wireless driver. And the computer recognizes it. However, when you click on it, it shows three drivers and says "Hardware present: No". And it *still* won't recognize my home wifi network. 

She thought I would just need a key combination to enable wireless communication. I checked my manual. That combination is Fn+F8. I tried it. Nothing happens.

Any help? Please. I'm so sick of this. I don't want to spend another thirty five bucks, but it's looking like I'll have to.

Thanks for any help.

---

### Post by walt.smith1960 on 2011-01-30
Have you tried connecting to any wireless network beside your home network?  Such as StarBucks, McDonalds, local library etc.? Although if you're seeing 'hardware present:no' that probably won't matter.

How are you seeing 3 drivers?  

The key combination used to enable or disable wireless in Windows may work in Ubuntu, or it may not. Do you have a wireless networks section in Network Manager? If so, I assume you've right clicked on network manager and "enable networking" & "enable wireless" are both checked?

I had one other ugly thought.  On some systems, Windows disables network adapters on shutdown and the only way to re-enable the network adapter is through windows.  You need to change a setting in windows so it doesn't disable the network adapter on shutdown.  If this is the case on your machine and you lost windows, you may have no way to to activate your internal wireless adapter except to reinstall windows. If this were the case, you could buy a USB adapter that's known to work and use that but it probably makes better sense to spend the money to reinstall windows.

---

### Post by b0b138 on 2011-01-30
Hmmm...ok lets start with some basics. I'm going to assume you have hopefully done this a thousand times now, but, one more can't hurt ;)

1. Have you actually installed to the hdd, not a live session?

2. Go into the bios and make sure that the wifi adapter is enabled.

3. Does it have a switch somewhere, on the side maybe, that enables/disables the wireless? I know some notebooks do.

4. Post the output of lspci. I know it will probably show 2 network adapters. Which is good, at least it can see the hardware.

5. According to that other thread, that repo should have worked. Have you tried again after a full install? ```
sudo add-apt-repository ppa:lexical/hwe-wireless
apt-get update
apt-get install rtl8192ce-dkms
```

6. Plan B: Get a windows disk from "somewhere". Even without a key, you can install and run long enough to see if it can use the wifi and rule out a hardware problem. And if what walt said crazily happened, you will also be able to reverse the disable on shutdown thing.


Just found this [https://bbs.archlinux.org/viewtopic.php?id=109688](https://bbs.archlinux.org/viewtopic.php?id=109688)   Driver from realtek for linux for that chipset. Just have to compile it

---

### Post by pencils42 on 2011-01-30
> **b0b138 said:**
> Hmmm...ok lets start with some basics. I'm going to assume you have hopefully done this a thousand times now, but, one more can't hurt ;)

1. Have you actually installed to the hdd, not a live session?

2. Go into the bios and make sure that the wifi adapter is enabled.

3. Does it have a switch somewhere, on the side maybe, that enables/disables the wireless? I know some notebooks do.

4. Post the output of lspci. I know it will probably show 2 network adapters. Which is good, at least it can see the hardware.

5. According to that other thread, that repo should have worked. Have you tried again after a full install? ```
sudo add-apt-repository ppa:lexical/hwe-wireless
apt-get update
apt-get install rtl8192ce-dkms
```6. Plan B: Get a windows disk from "somewhere". Even without a key, you can install and run long enough to see if it can use the wifi and rule out a hardware problem. And if what walt said crazily happened, you will also be able to reverse the disable on shutdown thing.


Just found this [https://bbs.archlinux.org/viewtopic.php?id=109688](https://bbs.archlinux.org/viewtopic.php?id=109688)   Driver from realtek for linux for that chipset. Just have to compile it

1. Yep:)
2. Done, it is.
3. The only wireless on and off I can find based on the manual is Fn+F8, which, unfortunately, does nothing.
4. 0:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
5. I put in the commands you suggested too, no luck. As for the last part of your suggestion, I already have the correct wireless driver installed, a computer consultant did it for me. It just says the hardware isn't present and doesn't recognize *any* Wifi networks.

I do appreciate everyone's help.

---

### Post by uRock on 2011-01-30
Have you installed the Linux Firemware Nonfree package? That may be all you need to get things working.

```
sudo apt-get install linux-firmware-nonfree
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175501&d=1289660118[/IMG]

Best of wishes,
uRock

---

### Post by pencils42 on 2011-01-31
> **uRock said:**
> Have you installed the Linux Firemware Nonfree package? That may be all you need to get things working.

```
sudo apt-get install linux-firmware-nonfree
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175501&d=1289660118[/IMG]

Best of wishes,
uRock

Tried it. It appeared to install, but, to be frank, nothing happened.

---

### Post by J-Logger on 2011-01-31
So, this is the "Absolute Beginner" Thread, right?  Please do not be offended, but... make sure it is turned on.  I have a Dell D600 and I spent about 3 hours one night on the same problem until I found a little slide switch on the side.  Somewhere on your computer there will be a little light that says wireless, wifi, etc.  Make sure it is on...

Jim

---

### Post by walt.smith1960 on 2011-01-31
> **J-Logger said:**
> So, this is the "Absolute Beginner" Thread, right?  Please do not be offended, but... make sure it is turned on.  I have a Dell D600 and I spent about 3 hours one night on the same problem until I found a little slide switch on the side.  Somewhere on your computer there will be a little light that says wireless, wifi, etc.  Make sure it is on...

Jim

On a similar note--A friend bought a new HP notebook this Christmas and asked me to help set it up.  It had an LED built into the  function key that controlled WiFi. Amber=off, white=on.  I COULD NOT get that LED to change from amber to white.  I was trying a 2 key combination.  I changed something in the BIOS setting and saw a setting to change the hardware control functions on the F keys on the top of the keyboard.  The default was to press one key for hardware control, press a 2 key combination for F1-F12 functions-the opposite of what I was used to.  That might be something else to try.

---

