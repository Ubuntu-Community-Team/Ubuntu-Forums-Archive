---
title: "Having trouble with two things."
date: 2010-06-15
forum: New to Ubuntu
---

### Post by ATPJOE on 2010-06-15
I've been working out the kinks that I've come across (swappiness, stuff like that) but can't solve these:

1. Trackpoint sensitivity and speed settings won't stick after reboot. Sucks so much *** using the nub when they're at default.

2. All video playback is suddenly choppy and slow. Youtube, and files from my PC do this. 

3. Sound sometimes has to be "woken up". Easy fix, just would be nice if it didn't do it period.

I'm getting pretty good with terminal again so throw whatever code at me as long as it won't torch my OS. :p

---

### Post by bswilson on 2010-06-15
Your profile indicates you're using Karmic.  Have you considered upgrading to Lucid to see if your 3 issues are resolved?

---

### Post by Bucky Ball on 2010-06-15
> **bswilson said:**
> Your profile indicates you're using Karmic.  Have you considered upgrading to Lucid to see if your 3 issues are resolved?

HAHa! Good luck with that fix! But you never know, it might just work. Then again, you might end up with a lot more problems than you started with. ;)

---

### Post by sandyd on 2010-06-15
> **ATPJOE said:**
> I've been working out the kinks that I've come across (swappiness, stuff like that) but can't solve these:

1. Trackpoint sensitivity and speed settings won't stick after reboot. Sucks so much *** using the nub when they're at default.
[B]I know eh?
this thing really bugged me as the pointer simply whizzed all over the screen...

anyways...
```

gksudo gedit /etc/apt/sources.list

```add to the end of the file[/B]```
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/speed 
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
```2. All video playback is suddenly choppy and slow. Youtube, and files from my PC do this. 
**Whats your video card?**
[B]```

lspci
```[/B]

3. Sound sometimes has to be "woken up". Easy fix, just would be nice if it didn't do it period.
[B]Try ```

pulseaudio -k
```[/B] 
I'm getting pretty good with terminal again so throw whatever code at me as long as it won't torch my OS. :p
not bad provided im preparing to go on tour...

---

### Post by ATPJOE on 2010-06-16
> **bswilson said:**
> Your profile indicates you're using Karmic.  Have you considered upgrading to Lucid to see if your 3 issues are resolved?

I have 10.04, I forgot to update my profile. Will fix that asap.

> **carlee said:**
> not bad provided im preparing to go on tour...

Rebooting now to find out if the Trackpoint settings stick...
EDIT: Didn't work. However I removed the /serio2/ from the path because I don't have that folder, my speed and sensitivity files are just in /serio1/. Should I include serio2 regardless?

I can't tell which one exactly is the graphics card so here's the whole mess:
```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

As for the audio suggestion:
```
root@Thinkpad:/home/joe# pulseaudio -k
E: main.c: Failed to kill daemon: No such process

```

---

### Post by Bucky Ball on 2010-06-16
Do you have Applications->Sound and Vid->Pulse Audio Device Chooser?

---

### Post by ATPJOE on 2010-06-16
No, nothing Pulse related in there.

---

### Post by sandyd on 2010-06-16
> **ATPJOE said:**
> I have 10.04, I forgot to update my profile. Will fix that asap.



Rebooting now to find out if the Trackpoint settings stick...
EDIT: Didn't work. However I removed the /serio2/ from the path because I don't have that folder, my speed and sensitivity files are just in /serio1/. Should I include serio2 regardless?

I can't tell which one exactly is the graphics card so here's the whole mess:
```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
**01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)**
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```
**This video card is currently problamatic. Theirs a couple of threads here on ubuntuforums, and a couple more discussions on kernel.org, but none have a definate answer.**

As for the audio suggestion:
```
root@Thinkpad:/home/joe# pulseaudio -k
E: main.c: Failed to kill daemon: No such process

```
and tell me, are you running x64 or 32bit ubuntu?

---

### Post by ATPJOE on 2010-06-17
32bit I'm pretty sure. I figured this laptop's graphics were just weak...they weren't great on Windows...however they were never this bad.

---

