---
title: "Sound is spotty at best."
date: 2009-01-14
forum: New to Ubuntu
---

### Post by djk21108 on 2009-01-14
Hi, recent Ubuntu installee.  My sound sometime cuts out for no reason.  I'm playing along musics going, pidgins making noise, next thing i know no sound.

I think it might have to do with java things open in firefox.  even when i close firefox though, the sound problems persist.

help!!

---

### Post by Crafty Kisses on 2009-01-15
What are the results of this command?
```
lspci
```

---

### Post by djk21108 on 2009-01-15
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by Crafty Kisses on 2009-01-15
Sorry I didn't ask this in my original post, but what are your system specs?

---

### Post by djk21108 on 2009-01-15
core 2 duo 2 ghz
2 gb ram
x1400 mobility ati graphics card

anything else?

---

### Post by djk21108 on 2009-01-15
ya there pal?

---

### Post by Vantrax on 2009-01-15
Is your sound set to pulse-audio or alsa mixer?

The intel audio devices are well supported so I will be surprised if its a driver issue.

---

### Post by djk21108 on 2009-01-15
I'm still having this problem.  My sounds not muted, but I can't hear anything at all.

---

### Post by djk21108 on 2009-01-15
Someone saveeee me.

---

### Post by djk21108 on 2009-01-15
help, anyone!

---

### Post by mikeysfbay on 2009-01-22
I have to say, finding an answer to these soundcard problems is like looking for a needle in a haystack for newbies like myself.  I see this thread ended up nowhere.  The "Comprehensive Guide" regarding sound left me in a tornado of guesses.
This is what my terminal answers to aplay -l:

card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  
This card performed beautifully while I was using Windows.  Since the switch to Ubuntu, sounds are "spotty at best."  Now I see a reference to "Kubuntu" and "Xubuntu"...I'm only assuming these were included in the 8.10 disc upload?  

I'll keep trying, but...man, what a roundabout way to restore my sound quality.

---

### Post by markbuntu on 2009-01-22
Due to the screwing around by OEMs of the HDA sound chip firmware it is very difficult to get a lot of these chips working since automatic detection can only go so far. That said, there are a number of threads dedicated to helping people find the right option for the snd_hda_intel driver.

You should look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

[http://ubuntuforums.org/showthread.php?t=1013750](http://ubuntuforums.org/showthread.php?t=1013750)

I am also trying to get a database together of snd_hda_intel options by make and model. If you have figured out the proper option for your make and model of laptop or for your motherboard and it is not on the list, please post the info in the thread linked below and I will add it to the OP.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by mikeysfbay on 2009-01-23
Before I go read these, just wanted to thank you very, very much for taking the time to post.  Seriously. I'm overwhelmed!  Best wishes...

---

