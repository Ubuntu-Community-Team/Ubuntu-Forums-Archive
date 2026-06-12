---
title: "Hardy doesn't recognize Broadcom wireless ada[ter"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by doriard on 2008-04-24
I installed Hardy on my HP9408nr laptop with 4BCM94311MCG Broadcom wireless, but no wireless adapter is even recognized.  I tried using ndiswrapper following instructions in the development forum, but it didn't do anything, and I'm not sure if the installation worked.  Since that didn't work, I uninstalled ndiswrapper and installed b43-fwcutter.  Still doesn't work.  I tried installing Wicd to see if would make it easier to recognize what was going on, but Wicd doesn't show any wireless interfaces present.  What do I do next?

---

### Post by knaveman on 2008-04-24
This won't make you feel any better but I have had the same problem with hardy for some time now. The only thing I came up with was to wait until the devs sort it out. Or use a usb adapter. Yeah, it pretty much sucks.

---

### Post by Tim Sharitt on 2008-04-24
After you installer b43-fwcutter did you enable the b43 driver in the driver manager (System > Administration > Hardware Drivers in gnome, not sure where it's at in kde)? Also, I'm not sure this is an issue but, when I upgraded to Hardy beta b43-fwcutter didn't seem to work when installed from synaptic but worked fine from aptitude (I was told it was to do with the installer downloading the firmware, I can't say for sure).

---

### Post by doriard on 2008-04-24
There is no "Hardware drivers" showing up under System/Administration in Kubuntu.  In Kubuntu I think it usually shows up as "Restricted Drivers" in System/Administration, but that is not showing up either.  On my desktop computer with Hardy and Nvidia video drivers, when I installed the video drivers, Hardy automatically created the "Restricted Drivers" icon in System/Administration, and then automatically applied the drivers.  I'm guessing it would be similar for the Broadcom drivers.  Even though b43-fwcutter driver is installed, it's not being recognized.  So maybe the next stop is to figure out how to get Hardy to recognize that the b43-fwcutter driver is installed and enable it...??

---

### Post by cob on 2008-04-24
I cannot believe that we are still battling the Broadcom wireless issue after all these years.  I understand that this is mostly Broadcom's fault for not offering details needed to create a free driver or providing their own closed driver, but there are ways around it, and the time spent on it shouldn't be on the user end on every release.

---

