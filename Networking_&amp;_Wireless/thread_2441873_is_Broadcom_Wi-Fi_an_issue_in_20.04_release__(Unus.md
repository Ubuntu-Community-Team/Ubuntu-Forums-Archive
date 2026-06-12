---
title: "is Broadcom Wi-Fi an issue in 20.04 release?  (Unusual error message...)"
date: 2020-04-27
forum: Networking &amp; Wireless
---

### Post by anotherChris on 2020-04-27
Background: I had issues with the Broadcom Wi-Fi in my Dell Inspiron 1545 laptop previously.  They were fixed by downloading some firmware.  (More specifics [in this thread]("https://ubuntuforums.org/showthread.php?t=2310798"). )

I am currently running Lubuntu 17.10, and when I upgraded from 15 to 17, I had no issues that required re-installing Broadcom Wi-Fi firmware per the linked thread above.  Somewhere I read that in 17.10 the Broadcom wireless was not an issue any more, although I don't know where I was told that.

Now, I want to install Lubuntu 20.04.

I have put the .iso on a USB stick and booted 20.04 several times.  Each time, I get different messages on boot or shut down.  Most recently, I got several lines starting with the following:

> [COLOR=#203243][FONT=Helvetica][ 97.605515] b43-phy0 ERROR: Firmware file “b43/ucode15.fw” not found.[/FONT][/COLOR]

So, b43 means an issue with the Broadcom, right?.  However, I am not sure what's going on.  The problem is that if I install 20.04 and lose Wi-Fi afterwards, I may be screwed.

Does the error message mean I actually lost that "ucode15.fw" file, or did the message occur only because I was booting from a USB (I have never done that before), meaning if I actually install 20.04, I won't have any issues with needing to install Broadcom b43 files again?

I have the USB stick that I used to fix the b43 issue last time.  The ZIP and the command line commands I need are all on it.  If I install 20.04 and my Wi-Fi doesn't work, can I use the same files and installation commands that I did last time to fix the issue, or does the new OS mean I need different files and/or commands to fix it?

I hope my problem is clear.  Please help.

---

### Post by jeremy31 on 2020-04-27
Moved to Networking & Wireless
Before installing use the driver manager to install the firmware-b43-installer and when installing allow installing of third party software and with a little luck the installer will install the firmware

---

### Post by wildmanne39 on 2020-04-27
It means the firmware needs to be installed, it does not come installed in ubuntu for legal reasons, but to help we need more information.

Hi, please click on the wireless script in my signature, follow the directions to run it and post the results back here using the pastebin link created. 

If you are running 17.10 the best thing to do is back up your data and do a clean install instead of trying to upgrade from a version of ubuntu that is EOL, if you do an upgrade then it should preserve your files and you will not need to reinstall the firmware, running from an iso you do for sure.

Edit:
You can always use a cell phone with a hotspot and tether to your computer to install the firmware if needed or you can download the needed firmware to a usb drive then put it on your computer, no need to panic, I am referring to your post in the other thread its not as bad as you think.

---

### Post by anotherChris on 2020-04-27
> [COLOR=#000000]It means the firmware needs to be installed, it does not come installed in ubuntu for legal reasons, but to help we need more information.[/COLOR]

Yes, but as I mentioned above, it was not an issue when I installed 17.10, and at that time I was told it was "fixed" and would not be an issue in the future.

From my previous post:

> 
[COLOR=#000000]computer: Dell Inspiron 1545 2GB RAM 160GB memory Lubuntu 11.10[/COLOR]
[COLOR=#000000]wireless: [/COLOR][B]BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
kernel driver: b43-pci-bridge
[/B]

Which means I should need "[COLOR=#000000][FONT=&amp]firmware-b43-installer[/FONT][/COLOR]

I have the ZIP, files, and instructions from the last time I installed b43 installer, but do I need it again?   Do I need different files now?    If I install 20.04 now, am I going to lose Wi-Fi?

> [COLOR=#000000]If you are running 17.10 the best thing to do is back up your data and do a clean install [/COLOR]

Yes, that is what I am trying to do.  But I think I did a clean install of 17.10, too, and did not need to do anything with Broadcom Wi-Fi...

(BTW, I tried to do the pastbin thing, but Chrome wouldn't let me post.  I have never had that issue before, but said it detected something and would not let me post--the Chrome browser did...)

---

### Post by jeremy31 on 2020-04-27
The files haven't changed names for quite a while.  If you want you can make a copy of /lib/firmware/b43 just in case it doesn't install on 20.04, then you would just have to create the b43 directory in /lib/firmware/ and copy the files

I found an old post that actually should still work [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)

---

### Post by anotherChris on 2020-04-27
.

---

### Post by anotherChris on 2020-04-27
Yeah, I think that's what I did before.  But I didn't have to do any of this when I installed 17.10!   What gives?   And is this something I have to do offline every time I install a new LTS?

---

### Post by jeremy31 on 2020-04-27
I think it has to do with allowing third party software during the install as the files to install the firmware are on the ISO.  I tested it on 18.04 ISO with the broadcom proprietary module and it was installed on the hard drive

---

### Post by anotherChris on 2020-04-27
Okay.  Good to know.  Will try.  Thank you.

---

### Post by anotherChris on 2020-04-29
Thank you.  I installed Lubuntu 20.04 yesterday.  It didn' t have any Wi-Fi, but I installed firmware from USB by instructions at the following links, and it worked very well...

[https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)

[https://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843](https://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843)

Thanks for everyone's help.

---

