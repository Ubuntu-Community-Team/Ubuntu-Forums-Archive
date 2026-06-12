---
title: "Videos absolutely will not play in Jaunty!!"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by ambs5702 on 2009-06-13
[FONT=Georgia]My brother installed Ubuntu 9.04 on my Acer Aspire 1640Z series laptop. So far I absolutely hate it. It will not play videos. Most pictures don't load on webpages. Its just ridiculous. I have installed flash player & that doesn't work. I have tried every program that I could find to try & convert Windows programs thinking maybe that would help. Nothing. I'm getting really irritated.

I would really appreciate any help on why the videos/pictures don't load. & a solution would be extremely helpful. Please? =)
[/FONT]

---

### Post by overdrank on 2009-06-13
> **ambs5702 said:**
> [FONT=Georgia]My brother installed Ubuntu 9.04 on my Acer Aspire 1640Z series laptop. So far I absolutely hate it. It will not play videos. Most pictures don't load on webpages. Its just ridiculous. I have installed flash player & that doesn't work. I have tried every program that I could find to try & convert Windows programs thinking maybe that would help. Nothing. I'm getting really irritated.

I would really appreciate any help on why the videos/pictures don't load. & a solution would be extremely helpful. Please? =)
[/FONT]

Hi and welcome,  have you installed the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
You may also check if your graphics need drivers, under system, administration, Hardware driver.
Moved to Absolute Beginner Talk

---

### Post by kmg90 on 2009-06-13
also which version of ubuntu did you install?

32 or 64 bit?

---

### Post by Sarai the Geek on 2009-06-13
Try installing the restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

After restarting, if that doesn't work it could potentially be a graphics card problem? Post the output of:

```
lspci | grep VGA
```

---

### Post by ambs5702 on 2009-06-13
I have tried the restricted extras in the past & it wouldn't work, this link did however. I checked the hardware & there is nothing. What should I do?

Also, I have no idea what bit i have. How would I check?
I have no idea about anything that has to do w/ linux or ubuntu. =)

---

### Post by sandyd on 2009-06-13
> **ambs5702 said:**
> I have tried the restricted extras in the past & it wouldn't work, this link did however. I checked the hardware & there is nothing. What should I do?

Also, I have no idea what bit i have. How would I check?
I have no idea about anything that has to do w/ linux or ubuntu. =)

type this in the terminal to check the bit
```

uname -a

```

then post the output of 
```

lspci

```

---

### Post by ambs5702 on 2009-06-13
amber@amber-laptop:~$ uname -a
Linux amber-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
amber@amber-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
amber@amber-laptop:~$ 



this is what I got. still have no idea what my bit is?
so would the bit have anything to do with why i have absolutely no "proprietary drivers" installed?

My laptop will play mp3's & dvd's. but nothing on the internet.

---

### Post by sandyd on 2009-06-13
some info for ya

its a 32 bit lappy 
```

Linux amber-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 **i686** GNU/Linux

```

and the video card is
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

```

---

### Post by QIII on 2009-06-13
This might be worth a look.


[http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video+regression](http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video+regression)

---

### Post by Sarai the Geek on 2009-06-13
You have a 32bit install and an Intel 915GM/GMS/910GML graphics card. :)

It s*ounds* like your flash plugin isn't working- how did you install it? (i.e. which package did you download?)

---

### Post by ambs5702 on 2009-06-13
I currently have version 10 installed.
I read somewhere that version 9 would work better, but when I downloaded that i got a document, no installation software. Unless there is a code I have to enter there too. I'm so confused lol.

I'm not ready to give up on ubuntu just yet!

---

### Post by esalnoj on 2009-06-13
Enclosed is a thread link for intel driver support in jaunty.

<http://ubuntuforums.org/showthread.php?t=1130582>

Enjoy.

---

