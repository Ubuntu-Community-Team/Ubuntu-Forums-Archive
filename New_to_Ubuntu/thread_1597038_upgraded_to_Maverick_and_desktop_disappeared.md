---
title: "upgraded to Maverick and desktop disappeared"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by beew on 2010-10-14
After upgrading from Lucid to Maverick in my (test) installation I seem to have lost the gui. I used the update manager for upgrading, when restarted the computer booted into the terminal.

I typed startx and I got

> dopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
(EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available
               

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
  at [http://wiki.x.org](http://wiki.x.org)
for help

 ddxSigGiveUp: Closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno3): Server error.I have a Nvidia card and the Nvidia driver was in use before the upgrade.

Thanks for any help in advance.

---

### Post by beew on 2010-10-15
bump?

Sorry if I am bumping too soon, but since my access to the internet is kind of shaky for these few days have to do it when i have a chance. :)

---

### Post by AndyM3 on 2010-10-15
Try installing the Nouveau driver.
```
sudo apt-get install xserver-xorg-video-nouveau
```

---

### Post by crowderd on 2010-10-15
> **AndyM3 said:**
> Try installing the Nouveau driver.
```
sudo apt-get install xserver-xorg-video-nouveau
```


I just did this as well and Im getting just about the same error... I have a lenovo with intel chipset so will this work for me as well?

---

### Post by cariboo on 2010-10-15
I have a feeling that the graphics driver isn't getting upgraded properly, I would suggest you remove /etc/X11/xorg.conf, and restart. It should now take you to the Desktop, where you can install the latest nvidia driver. There was a change in Xorg, so the older drivers don't seem to work properly.

---

### Post by beew on 2010-10-16
> **AndyM3 said:**
> Try installing the Nouveau driver.
```
sudo apt-get install xserver-xorg-video-nouveau
```

I just did this and it says it already has the newest version installed.

---

### Post by beew on 2010-10-16
> **cariboo907 said:**
> I have a feeling that the graphics driver isn't getting upgraded properly, I would suggest you remove /etc/X11/xorg.conf, and restart. It should now take you to the Desktop, where you can install the latest nvidia driver. There was a change in Xorg, so the older drivers don't seem to work properly.


This works! Thanks a million cariboo907. Today I learn something new and important!!

---

### Post by beew on 2010-10-16
Opps, I was happy too soon, good that I didn't mark the thread as solved. 

After removing /etc/X11/xorg.conf (how come some people say the file no longer exists for newer version of Ubuntu???) I was able to boot into the Desktop, the Nvidia card apparently was still installed but the resolution was not right. I tried to fix it and the Nvidia setting manager said that the Nvidia card was not in use and that I had to run sudo nvidia-xorgconfig. I did that and rebooted but I was in text mode again. So I removed /etc/X11/xorg.conf again and booted into the desktop. 

I thought I should reinstall the Nvidia driver, I removed it from Synaptic and reboot. In Lucid I would simply go to "Hardware Drivers" and it would take care of it. 

But "Additonal Drivers" in Maverick did not "see" the Nvidia card. I think that is the crux of the problem because it indicates that support for this card may be poor in Maverick while it works almost out of the box in Lucid. 

So I installed the drivers from Synaptic and it was only after that that "additional driver" picked out the Nvidia card and asked me if I wanted to activated it.

I activated it and rebooted but the graphic remained horrendous (Nvidia driver not in use), so I run nvidia-xconfig in the terminal and restarted, but once again I booted into text mold.

So long story short, I just can't install the Nvidia driver in Maverick in the same way I did in Lucid.  In Lucid there was no need to run "nvidia-xorgconfig", activating in "Hardware drivers" and reboot is all that is required. But in Maverick 1) additional driver doesn't sniff out the Nvidia card 2) When the driver is installed you have to run "nvidia-xorgconf" 3) the result of running "nvidia-xorgconf" would be to boot into text mode.

---

### Post by beew on 2010-10-16
This seems to be a problem only with the Nvidia-96 driver. In a newer machine Maverick's "Additional Hardwares" module picked up the Nvidia card with no problem,--however when reboot I got some error message about plymouth  and the terminal login line appears briefly before booting into the desktop.

I had not have problems with Nvidia card with Lucid, I am not sure what they had done with Maverick but now there appears to be some wrinkles even when it works (with the plymouth error and brief appearance of the terminal at boot)

---

### Post by maniaq on 2010-10-18
it's the new version of xorg they've put into Maverick - had nothing but trouble on two different machines - one with an ati card and the other with an nvidia - after upgrading distro, neither will work unless I completely remove the closed-source drivers 

-which means I'm stuck with the not-as-good open-source versions...

---

### Post by muteXe on 2010-10-18
What was wrong with 10.04?

---

### Post by beew on 2010-10-18
> **muteXe said:**
> What was wrong with 10.04?

Nothing, Lucid is almost perfect.  But I want to find out what is new in 10.10. It seems that it uses less cpu in things like flash and an annoying problem in Lucid for vlc is fixed (a hiccup like sound in the beginning of some mp3 files) 

But Maverick have problems with some legacy drivers, most notably Nvidia -96 and Synaptic also feezes quite often though that may be a hard drive problem.

I however don't like the idea of staying indefinitely in "the version that works" and hold off upgrading for fear that something will screw up. Tthere is something very wrong with Ubuntu and Canonical if it is taken for granted that upgrading will break something crucial. If that is taken to be a given you can't really consider Ubuntu to be a serious OS.

---

