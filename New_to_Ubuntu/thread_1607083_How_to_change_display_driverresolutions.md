---
title: "How to change display driver/resolutions?"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by mc510 on 2010-10-27
Display isn't working properly on new 10.10 installation (heavy flickering; wrong resolution) with Nvidia MX440 graphics.  I gather that it must be using either nv or nouveau driver, so I figure I should try the other one.  But I can't tell which is in use or how I would change from one to the other.

---

### Post by Silent Warrior on 2010-10-27
If you start Hardware Drivers ('jockey' at the terminal), what does it show? Another way would be to install lshw-gui and look at the Hardware Lister. I forget where exactly they're found - I'm on Mint, and in any case haven't had problems like these for a looooooooong time now. Also, I don't know how well that card handles composite graphics. Look for Desktop Effects (possibly in Appearance, otherwise it's CompizConfig) and disable them to see if that's the cause of the flickering.

One sure-fire way to use one driver and not the other is also to uninstall one of them. I wouldn't recommend it, though - if you're stuck with the wrong driver, the results will be... scary. Fully reparable - I might even be able to walk you through that - but scary none the less.

---

### Post by ivarn on 2010-10-27
Since this is a NVIDIA X server problem, go to nvidia x server settings and display settings.
Or you can follow this guide and do the changes manually.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by mc510 on 2010-10-27
ivarn, I tried that guide for manually editing xorg.conf, but that file no longer exists (at least not in that location) in Maverick.  

Since I'm not using (or able to use) the Nvidia proprietary driver, would the Nvidia configuration tool still be useful?  I'm certain that I'm using either nv or nouveau, though I have no way to tell which.

I'm willing to try manually editing xorg.conf, but I can't figure out where it is or how to do it in Maverick.

I haven't had a chance yet to try the solutions that Silent Warrior mentioned.

---

### Post by Terl on 2010-10-27
Some googling found this: [http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/]("http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/")

It is an old card and support is fading for it so if you could upgrade you may want to look into it...

---

### Post by mc510 on 2010-10-27
Thanks gang, here's an update:

Desktop effects are not enabled.

I installed lshw-gtk ... it tells me that I am using nouveau driver.  Since it's not working right, I'd like to try nv, but:

Ubuntu Software Center tells me that nv is already installed.  But I have no idea how to select it, since there is no xorg.conf file anymore.

Terl's link says to run nvidia-xconfig, but I don't have that program, and it's not available in the Ubuntu Software Center.  It's probably installed along with the Nvidia binary driver, but that driver is currently not available for NV18.

All I want to do is to switch from nouveau to nv, and also to be able to have the correct screen resolution.  This used to be easy when xorg.conf was around; now it seems that there is just no way at all to do it?

---

