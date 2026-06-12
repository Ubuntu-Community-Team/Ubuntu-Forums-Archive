---
title: "No ethernet or wifi -bcm4306"
date: 2015-03-15
forum: Networking &amp; Wireless
---

### Post by tanner4 on 2015-03-15
Hey guys,
I'm no expert with computers, so I'll give you as much information as I can and go from there.
I have an HP pavilion dv1000 that I just put lubuntu 14.10 on as a dual-boot alongside Windows XP. I had to use WUBI (a version posted by someone on here) to install it because the laptop's usb ports and disk drive aren't working (that's the next challenge after getting internet working).
The Ethernet doesn't connect. I ran lspci in the terminal and it says the Ethernet controller is a "Realtek Semiconductor". I don't know if that helps.
The wifi, Broadcom BCM4306, doesn't connect either. It worked just fine in XP. Also, there's this wifi toggle button on the top right of the keyboard. Its supposed to light up, but it doesn't.
Final note, I tried running rfkill list and all it did was move to a new line. Sudo rfkill unblock all didn't do anything to solve the problem either.
Its driving me nuts

All input is appreciated. 
Thanks

---

### Post by hakuna_matata on 2015-03-15
Hey tanner4,

welcome to the forums.

> **tanner4 said:**
> The wifi, Broadcom BCM4306, doesn't connect either.
IMHO Broadcom BCM4306 needs a special firmware: [URL="http://ubuntuforums.org/showthread.php?t=2214110"]http://ubuntuforums.org/showthread.php?t=221411
[/URL]

---

### Post by tanner4 on 2015-03-15
Thanks hakuna-matata. Sounds like the new firmware should fix the issues I'm having with wireless. I guess now I need to get my wired internet working so I can install the firmware.
I just checked, and the ethernet doesn't work even when booted to XP. Looks like that's not just a problem from switching to Ubuntu. I'll see if I can get that going, and then work from there.

BTW, thanks a ton for the working version of wubi, hakuna-matata.

---

### Post by wildmanne39 on 2015-03-16
Download the file to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. 

Open a terminal and do:

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43_updated.zip/*  /lib/firmware/b43
sudo modprobe -rv b43 
sudo modprobe -v b43
```
if it does not come on reboot.
Wireless should now be working.

[https://dl.dropboxusercontent.com/s/19e7y7w6ndozdzq/b43_updated.zip?dl=1&token_hash=AAEELVjeW3iSm3d0ScTg17BSplJ01qhPGCkhav5o9EYiJA&expiry=1400713892](https://dl.dropboxusercontent.com/s/19e7y7w6ndozdzq/b43_updated.zip?dl=1&token_hash=AAEELVjeW3iSm3d0ScTg17BSplJ01qhPGCkhav5o9EYiJA&expiry=1400713892)

Driver courtesy of chili555

---

### Post by hakuna_matata on 2015-03-16
> **tanner4 said:**
> I guess now I need to get my wired internet working so I can install the firmware.
As Wild Man described above you can install the firmware without working wired internet.
> **Wild Man said:**
> Download the file to a usb flash drive
If that is not possible because..
> **tanner4 said:**
> because the laptop's usb ports and disk drive aren't working
..you can download the file to a Windows partition (drive). At least one of these partitions is available at mount point **/host** (if you installed your Lubuntu with Wubi)

---

### Post by tanner4 on 2015-03-17
Thanks guys, I did what you guys said and it worked great!

---

### Post by wildmanne39 on 2015-03-17
Your welcome.
Enjoy!

---

