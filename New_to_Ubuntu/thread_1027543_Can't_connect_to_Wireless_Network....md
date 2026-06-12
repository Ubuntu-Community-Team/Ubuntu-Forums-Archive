---
title: "Can't connect to Wireless Network..."
date: 2009-01-01
forum: New to Ubuntu
---

### Post by NightmareShadow on 2009-01-01
Hello...
This is my first time here. Also first time Ubuntu user.
I got Windows Vista Business 32-bit installed too.

I just installed Ubuntu on my TOSHIBA Laptop. 
The installation went really quick and easy.

I logged in, so I tried to connect to the internet. But It didn't work.
It didn't detect the wireless network.

I have no problem at all connecting to wireless network in Windows.

I read all the help files and searched on [https://help.ubuntu.com/](https://help.ubuntu.com/).
It says to go to "System --> Administration --> Network" But in my Ubuntu, there is no "Network" button or anything.
There's only Network Tool or something like that. 

I tried rebooting and use do manual connection. No luck :(

Please assist me... 
Thank you.

---

### Post by ibizatunes on 2009-01-01
What version did you install 8.04 or 8.10?

---

### Post by NightmareShadow on 2009-01-01
I'm using Ubuntu Version 8.10...

---

### Post by NightmareShadow on 2009-01-01
Does anyone have an answer?

---

### Post by The Cog on 2009-01-01
There should be a network manager in your system tray which you can right-click to get properties etc. That is the first place to look.

Starting a command prompt and entering these commands: 
> iwconfig
lspci may produce information that can be helpful in diagnosing problems - post the output here.

---

### Post by NightmareShadow on 2009-01-01
> **The Cog said:**
> There should be a network manager in your system tray which you can right-click to get properties etc. That is the first place to look.

Starting a command prompt and entering these commands: 
 may produce information that can be helpful in diagnosing problems - post the output here.

Hi...This is the output:


```
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

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

and:
```

lo no wireless extensions.

eth0      
no wireless extensions.

pan0      
no wireless extensions.
```

---

### Post by DeeMenace on 2009-01-01
Hey i'm new at this but i had the same problem as you with a toshiba laptop also. is it a Satellite L305D-something ?

---

### Post by NightmareShadow on 2009-01-01
> **DeeMenace said:**
> Hey i'm new at this but i had the same problem as you with a toshiba laptop also. is it a Satellite L305D-something ?
Yes, I got the satellite version as well.

TOSHIBA Satellite Pro A200...

---

### Post by DeeMenace on 2009-01-01
I think i did something like this thread [http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d](http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d)  I can't find the original thread but it was a very similar process to whats on that thread. Hope that helps.

---

### Post by NightmareShadow on 2009-01-01
Hi, Thanks, I'll try that out(Once I rebooted)

---

### Post by NightmareShadow on 2009-01-01
Well, It certainly did not worked :(

---

### Post by DeeMenace on 2009-01-01
Do lspci in a terminal and see which network card you have post it back here .

---

### Post by NightmareShadow on 2009-01-01
> **DeeMenace said:**
> Do lspci in a terminal and see which network card you have post it back here .

Hi, I did that(In previous page)
Here it is:

```
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
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

Well, it couldn't be the network card problem. Because It works on Windows Vista

---

### Post by DeeMenace on 2009-01-01
Sorry I was away from the computer. Let me go check that laptop and make sure it is the same network card.

---

### Post by DeeMenace on 2009-01-01
Well that is the same Network card. This may be a silly question but did you go to system/administration/Hardware Drivers and enable the driver ? Do you even see it there ?

---

### Post by lkraemer on 2009-01-01
Google searching is your friend........Search for AR242x......
There should be a post by bmartin on HOWTO: AR242x


Open a Terminal window and use the following commands to verify the Wifi information.  It appears yours is a Atheros AR242x.

lspci

lspci -v | less

lsmod | grep ath

lshw -C Network

dmesg | grep -e iwl -e wlan -e ath

lspci -nn

iwconfig

iwlist scanning

1.  Go here and follow the steps to install the Wifi Drivers.
    8.04 = http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG
    8.10 = https://help.ubuntu.com/community/WifiDocs/Driver/Atheros
2.  If your Wifi still doesn't work try blacklisting the Restricted
    Hardware Drivers. 

sudo gedit /etc/modprobe.d/blacklist

#blacklist the Hardware Drivers (Restricted)
blacklist ath_hal
blacklist ath_pci

Save the file, and exit gedit.

Reboot and see if your Wifi is functional.
It worked on my Compaq CQ50-139NR running 8.04LTS.

lkraemer

---

### Post by NightmareShadow on 2009-01-02
> **DeeMenace said:**
> Well that is the same Network card. This may be a silly question but did you go to system/administration/Hardware Drivers and enable the driver ? Do you even see it there ?
Yes, I did go there, The driver was selected.

---

### Post by stchman on 2009-01-02
Install Intrepid's backport kernel modules as they have better Atheros support.

```
sudo apt-get install linux-backports-modules-intrepid-generic 
```

---

### Post by NightmareShadow on 2009-01-02
I tried all those method... It didn't worked. :(
Is there some kind of patch for this or something?

btw, this is weird: When I installed Ubuntu on VirtualBox, the WiFi worked fine. It detected and automatically connected to the internet.
I'm not going to use VirtualBox since it didn't detect my graphic cards etc..

---

### Post by The Cog on 2009-01-02
That's not weird. When you run an OS inside VirtualBox, it only sees the dummy hardware that VirtualBox pretends that it has. The dummy hardware is emulated and bears no relation to the real hardware in the box. The host OS drives the real hardware.

---

### Post by NightmareShadow on 2009-01-02
> **The Cog said:**
> That's not weird. When you run an OS inside VirtualBox, it only sees the dummy hardware that VirtualBox pretends that it has. The dummy hardware is emulated and bears no relation to the real hardware in the box. The host OS drives the real hardware.
Ah, So that's why it worked.

So, are there any solution to this?

---

### Post by The Cog on 2009-01-02
Well, I can see from lspci that you have an Atheros adapter:
> 04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
So that's what you need to be searching for. I can't help you further, I've never looked at Atheros, but they are quite common I think, so you should be able to find some instructions somewhere.

God luck.

---

### Post by wmdiem on 2009-01-02
you might have the atheros 5007 chipset which is a pain to make work. I used [http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi](http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi) to get mine working. There might be a more uptodate way if you are using 8.10 Doing a search on the forums for atheros 5007 should help you.

edit: turns out the above tutorial was yanked. [http://ubuntuforums.org/showthread.php?t=860314](http://ubuntuforums.org/showthread.php?t=860314) should be a good place to start.

---

### Post by NightmareShadow on 2009-01-02
> **wmdiem said:**
> you might have the atheros 5007 chipset which is a pain to make work. I used [http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi](http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi) to get mine working. There might be a more uptodate way if you are using 8.10 Doing a search on the forums for atheros 5007 should help you.

edit: turns out the above tutorial was yanked. [http://ubuntuforums.org/showthread.php?t=860314](http://ubuntuforums.org/showthread.php?t=860314) should be a good place to start.

Ok I'll read that through.

---

### Post by The Cog on 2009-01-02
I just noticed this thread's title. It looks like the same card you have and is marked as solved, so it may help.
[http://ubuntuforums.org/showthread.php?t=967654](http://ubuntuforums.org/showthread.php?t=967654)

---

### Post by NightmareShadow on 2009-01-17
Thank you very much for all help, but no hope for me :(
I had to remove Ubuntu as it didn't work.
I tried everything on post, spent about 1 and a half weeks trying to understand it. :(

Thanks...

---

### Post by seagullplayer77 on 2009-01-17
Try running lspci in a terminal window to see what kind of network card you have. Under Linux, not all cards work right out of the box; some of them require a little bit of tinkering before you can get them to function. Once you determine what kind of wireless card you have, it'll be easier to figure out how to get your wireless up and running.

---

### Post by beatrice on 2009-01-17
[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

Scroll down to the post by reasoner (no. #6) and follow the instructions. Hope it helps. It was the only thing that worked for me and I've spent quite a few days trying to make it work!

---

