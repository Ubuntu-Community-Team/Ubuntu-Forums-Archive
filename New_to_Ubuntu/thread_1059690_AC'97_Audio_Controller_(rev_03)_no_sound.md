---
title: "AC'97 Audio Controller (rev 03) no sound"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Grukmuck on 2009-02-04
ive done some quick searches on this here and there, but nothing really seams to pertain to me. the sound card is usually not the one i have.im not sure what to do about this no sound thing. the volume control tells me everything is turned up and not muted, but when i try to play a cd or watch videos on the internet (such as youtube) there is no sound. i dont even get error message sounds. im dual booting with windows xp and my sound works fine with that OS.

where can i go to make sure my sound card is supported, and if it is how do i go about getting it to work?

 im still new to linux and need all the help i can get. im really enjoying ubuntu so far and eager to learn.

lspci
```
 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

not having sound is stopping me from primarily booting into ubuntu because i often get lost in videos on the internet and like to listen to music while im messing about. so once i get it working i dont think i will be booting up XP for a while.

thanks

-gruk

---

### Post by Grukmuck on 2009-02-05
bump

---

### Post by 73ckn797 on 2009-02-05
See if the info in this link will be any help.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by spcwingo on 2009-02-05
Have you tried installing libflashsupport?

```
sudo apt-get install libflashsupport
```

It says it only works for flash 9, but I had a problem with one of my machines doing the same thing with flash 10.  A quick install of libflashsupport fixed it right up.  Although, I had to reboot for it to work.  If that doesn't work, you can remove libflashsupport like this:

```
sudo apt-get remove libflashsupport
```

Let us know how it goes.

---

### Post by Grukmuck on 2009-02-06
i checked here [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page") and i couldnt find my sound card, so im pretty sure that means  its not supported.

if that truly is the case, then am i just gonna have to deal with no sound, or is there some kind of work around?

---

### Post by spcwingo on 2009-02-06
I didn't read your first post right.  I didn't see the part about not being able to play CDs either.  I guess you could try ditching pulseaudio and go with straight ALSA or OSS.  Otherwise I would suggest hitting ebay and finding an old Soundblaster PCI card, assuming you have a desktop as opposed to a laptop. You'll also need an empty PCI slot.  If you go that route, you'll just have to go into your BIOS setup and disable the onboard sound if it is in fact an onboard model.

---

### Post by beswatcher on 2009-02-06
I have the same problem,except that My sound has been working for months since I installed Unbutu 8.04. After going from 8.04 2.6.24-22 to 2.6.24-23
I have no audio. I get this from the volume control;

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

I have the same Firefox plugins as before.

lspci shows me that there is a sound card.;

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

I'm not a beginner, but a slow learner. Any help would be appreciated.:(

---

### Post by 73ckn797 on 2009-02-06
I ran across this link. Check into it.
You might find info here:
[http://www.realtek.com.tw/faqs/faqsV...PFid=6&Level=3]("http://www.realtek.com.tw/faqs/faqsView.aspx?Langid=1&PFid=6&Level=3")

---

### Post by Grukmuck on 2009-02-06
no, i am on a laptop and not a desktop. im still not totally sure if its not supported or not, because ubuntu tells me that it knows its there. im thinking i might not have the right drivers or something. im gonna try some more things in that link that 73ckn797 posted first and see if that will work.



beswatcher: as im still very new to ubuntu and linux in general, i cant really offer any help, but my guess would be that you need to find out what, if any, GStreamer plugins your missing and install them. if you can figure out wich ones then it would probably be just a sudo apt-get install sort of deal. or if your not missing any plugins then you neeed to configure your soiund card and i dont know how to do that (heck, that might even be my problem, but i dunno). sorry that i couldnt give you any specifics, but thats just my take on it.

---

### Post by Grukmuck on 2009-02-10
i know its been a little while since i posted but school is taking up a lot of my time lately.

anyway, i was following the steps in that link that 73ckn797 posted earlier, and got this:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; module-assistant, interactive mode &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
       &#9474; Build of the package alsa-source failed! How do you wish to   &#9474; 
       &#9474; proceed?                                                      &#9474; 
       &#9474;                                                               &#9474; 
       &#9474;       VIEW     Examine the build log file                     &#9474; 
       &#9474;       CONTINUE Skip and continue with the next operation      &#9474; 
       &#9474;       STOP     Stop processing the build commands  

any help would be appreciated.

---

### Post by Grukmuck on 2009-02-11
bump

---

### Post by Grukmuck on 2009-02-14
bibidy bump

---

### Post by Grukmuck on 2009-02-18
bumpidy bump bump bump... bumpidy

---

### Post by Grukmuck on 2009-02-23
bump

---

### Post by repokill on 2009-02-25
same situation here

---

### Post by Grukmuck on 2009-02-26
well, i just killed the screen on my laptop (which is what i used the most). so now im stuck with just my desktop, which, incidentally has no speakers so i dont know if my sound works on that or not. im gonna do some tests with headphones and stuff.

---

### Post by cariboo on 2009-02-26
I guess it's a little to late now, but your sound should be supported out of the box. I have an 82801G, which is a later model than yours nad it worked out of the box. The sound driver is snd_hda_intel.

Jim

---

### Post by Grukmuck on 2009-02-26
mines 82801DB/DBL/DBM and i couldnt find a driver for it, so thats why i figured it wasnt supported.

---

