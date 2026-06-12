---
title: "display settings problem"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by artificialname on 2009-09-28
Just started with Ubuntu, and i'm loving it! My first successfull linux experience!

1 problem i can't fix:
I am using a Dell Laptop and i plugged in an external monitor. I changed the display settings so the monitor and the laptop screen did not "mirror" each other, so i could do things like drag a mozilla window onto the external screen and work on something different (not mozilla) on the laptop screen.

it worked well.

Then, suddenly, after restarting, it stopped working!
it switched back to normal (mirroring), so i set it up again, but then my panels disappeared off the top and bottom of my screen and the monitors were stuck mirroring each others blank screen (just the ubuntu background colour!). the only way to do anything (the "applications" menu had disappeared with the panels!) was to press FUNCTION-F8 which toggled the crt/lcd function on my laptop and returned both screens back to true mirrors, with panels.

any idea how to fix these display settings, so i can use my external monitor as a second screen?

thanks!

---

### Post by wojox on 2009-09-28
Open a terminal and post the output of:

```
lspci
```

---

### Post by artificialname on 2009-09-28
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller

---

### Post by humphreybc on 2009-09-28
Are you using Compiz or Metacity, and, are you using the free "radeon" drivers, or the closed-source Catalyst fglrx drivers?

ie. Go to Hardware Drivers and see if the driver is activated.

I had no luck getting dual screen to work with the closed source Catalyst drivers, so I switched to the open-source radeon drivers, and Metacity.

Basically, using Randr 1.2 I can hotplug my external monitor and using a virtual screen resolution set in the xorg.conf file, it will work perfectly. Fullscreen on either screen as well, not across both.

I highly suggest using the open source drivers instead of the ones provided by ATI, as I had a terrible experience with them. Although, I have heard that the latest drivers (9.9/9.10) have fixed a lot of problems (including the "Xinerama" option greyed out in CCC).

Have a look at my HowTO thread on ATI drivers here:

[http://ubuntuforums.org/showthread.php?t=1273767](http://ubuntuforums.org/showthread.php?t=1273767)

It might come in quite useful for choosing which drivers to go for.

---

### Post by CRAY-4 on 2009-09-28
did you install anything before the reboot(because thats a common problem)

---

### Post by overdrank on 2009-09-28
Hi and I have a similar laptop with the ati graphics and I suggest using xfix option in recovery mode. This may reconfigure your graphics driver to correct the issues.

---

### Post by artificialname on 2009-09-29
> **overdrank said:**
> Hi and I have a similar laptop with the ati graphics and I suggest using xfix option in recovery mode. This may reconfigure your graphics driver to correct the issues.

" I suggest using xfix option in recovery mode"

how do i do this?

---

### Post by overdrank on 2009-09-29
> **artificialname said:**
> " I suggest using xfix option in recovery mode"

how do i do this?

Hi and sorry for the delay in response. You can boot into recovery mode which is usually the second choice when booting from the grub. After completing xfix you should be given the option to boot normally.

---

### Post by artificialname on 2009-09-29
thanks
i tried xfix. 
no change

i'm confused by humphreybc's recommendations. what do i try next?

i think i tried to install azureus just before dual screen stopped working, but im not sure. it did not install properly - i was trying a "get" command from a terminal window. it did not work so i switched to using "transmission bit torrent client".

---

### Post by wojox on 2009-09-30
Look at humphreybc's how to on ati graphics

---

### Post by jward3010 on 2009-09-30
Type this in a terminal to go back to your default graphics configuration:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Do a restart and you should be back.

---

### Post by artificialname on 2009-10-08
hi 

thanks everyone for your tips.

i tried that SUDO command in jward3010 post.
It worked! for about 5 minutes. then stopped working! (i think it was when i pressed "function F8" to switch between screens that it stopped working)

Any ideas why?

I am a little scared of humphreybc's driver guide - I am a newbie! but if no one has any other ideas, I will work up the courage to try it!

thanks again!

---

### Post by henrodon on 2009-10-18
deleted -- problem changed and re-posted

---

