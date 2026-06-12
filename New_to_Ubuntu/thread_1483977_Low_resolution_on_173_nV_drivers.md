---
title: "Low resolution on 173 nV drivers"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by 96th on 2010-05-15
Hello. For the last couple of days I've been trying to make my Ubuntu usable. I have a nVidia GeForce FX 5500 on a AGP and a Samsung SyncMaster T200 screen. I have enabled the 173 driver and my resolution went down to 640x480 from 1024x768 that I had before nVidia drivers. I need the driver for 3D acceleration in games. Everything works fine on Debian 5, OpenSuSE 11.1 and Windows XP. On Windows I can get as high as 1650xsumthin', on OpenSuSE I can easily get 14xx by 900 and on Debian I can get 1280x800 with no problems. How can I get my Ubuntu to work propely? I want this to be my main OS, but resolution no bigger than some high-end phones is not helping.

---

### Post by TeoBigusGeekus on 2010-05-15
Open terminal and type
```
gksudo nvidia-settings
```
Go to X Server Display Configuration and change the resolution from there.

---

### Post by 96th on 2010-05-15
Sorry, I forgot about that. The only resolutions avialable there are: 640x480, 320x240. My old dumbphone can do better than that.

---

### Post by TeoBigusGeekus on 2010-05-15
When I enabled 3d acceleration, I had 3 choices for the drivers:
version 173
version 96
version current(Recommended)
I chose the current version and everything works fine.
Go to System->Administration->Hardware Drivers and see if you can get it as well.

---

### Post by 96th on 2010-05-15
I've only got 173 [reccomended] and 96...

---

### Post by TeoBigusGeekus on 2010-05-15
What happens if you choose 96?

---

### Post by 96th on 2010-05-15
It's still low and pretty much useless. Nothing has changed.

---

### Post by CaponeSA on 2010-05-16
Hi, see:

[http://ubuntuforums.org/showthread.php?t=1485110](http://ubuntuforums.org/showthread.php?t=1485110)

---

### Post by -humanaut- on 2010-05-16
The 96 Nvidia driver is for TNT cards the 173 Should be the right driver for an AGP port card try going to Monitor Settings see if you can acquire a resolution from there I'm surprised you can't access it from the Nvidia Settings screen.

---

### Post by 96th on 2010-05-17
So am I. It used to be very useful on SuSE and Debian. I cannot change it from there at all.

@CaponeSA: Now it just shows me a couple of lines at the top of my screen, like on VCR tapes. How do you get to the command line? CTRL+ALT+F2 doesn't work.

//Edit: This is a bloody disaster. My computer just overheated after 10 minutes of using it, and now it won't even go into failsafe.

---

