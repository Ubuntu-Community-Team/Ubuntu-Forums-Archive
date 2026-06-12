---
title: "No sound - ALSA appears broken"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by sparkiemark on 2009-02-14
At the end of my rope.  Sound is broken in my build of Ubuntu Hardy (8.04).  I have followed instructions at [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) to no avail.  It must be totally hosed, and I have no idea where to start.  Sound seemed to become an issue when I installed XBMC a few months back, and after months of tears, toil and Googling - no solution.  I am very shocked at how difficult it seems to configure sound in Ubuntu, judging from all the research I have conducted.

Any guidance will be greatly appreciated.

---

### Post by ilioscio on 2009-02-14
Okay, well I know you said you already tried everything in the guide, so sorry if I go over anything you've already done, but could you please post the output of 
```
aplay -l
```

---

### Post by TenPlus1 on 2009-02-14
Did you turn OFF Pulseaudio ? (untick service/session and reboot, that was screwing with my sound)...

---

### Post by listerdl on 2009-02-14
how do you turn off Pulseaudio? Where is the file located to change, is it in system>  ? thanks

---

### Post by sparkiemark on 2009-02-14
As requested:

sparkie@UbuntuHolmwood:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Here is my result for "lspci -v | less" as well

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Intel Corporation D865PERL mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at febff800 (32-bit, non-prefetchable) [size=512]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

This is exactly what I need is a walk-thru::P

---

### Post by sparkiemark on 2009-02-14
> **TenPlus1 said:**
> Did you turn OFF Pulseaudio ? (untick service/session and reboot, that was screwing with my sound)...

I selected System-->Preferences-->Sessions and unchecked "PulseAudio Session Management".  I rebooted and sound is now working for system sounds at least:P.  I opened up XBMC, however and still no sound.  This is a start at least.  I'm still not sure if everything is configured correctly.

---

### Post by ilioscio on 2009-02-14
play around inside Settings > System > Audio Hardware specifically. you should be able to get it working (hopefully) just messing around in there now.

---

### Post by sparkiemark on 2009-02-14
> **ilioscio said:**
> play around inside Settings > System > Audio Hardware specifically. you should be able to get it working (hopefully) just messing around in there now.

Thanks for everyone's help and support.  With the advice above, I got sound working:P. However, I discovered that only the PulseAudio Sound Server works in my Preferences-->Sound "Devices" options.  Whatever all apps have sound (including system sounds), except XBMC:confused:.  I am also posting on the XBMC forum for further advice on how to fix sound for XBMC.

Does anyone know why the little chain-link symbol on my Volume Control is broken under PCI??  See attached screenshot.

---

### Post by ilioscio on 2009-02-14
When the chain link is attached both the right and left audio sliders stay together but if you click on the chain and "break" it you can adjust you left and right channels to different levels (eg left speaker is louder than right or vice versa)

---

