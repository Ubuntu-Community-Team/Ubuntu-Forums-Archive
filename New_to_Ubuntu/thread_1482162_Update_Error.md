---
title: "Update Error"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by PPPilot on 2010-05-13
After running Karmic since December 2009, I decided to install Lucid in a separate partition on the same drive as Karmic so as not to mess up all my work to get Karmic running. All seemed to go well and Lucid seems to be running OK so far with the Lucid Grub running at boot. I am able to select and run either from GRUB. This AM I ran the Update Manager while in Karmic and got this message:

>  Please insert the disk labeled:
Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)
in drive /cdrom/I put in the Lucid CD and clicked OK and Nothing happened.
I noticed only 3 of the 7 available updates was checked. When I clicked Cancel, I get this error:  

> W: Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/b/build-essential/build-essential_11.4build1_i386.deb
  It will not allow me to check any of the four unchecked updates. Update Manager works OK in Lucid.

---

### Post by wojox on 2010-05-13
Open up sources.list

```
gksudo gedit /etc/apt/sources.list
```

And comment ( # ) out the cd-rom part at the top.

---

### Post by PPPilot on 2010-05-13
wojox,

Thanks a lot. That fixed the problem,,,,

---

### Post by wojox on 2010-05-13
Your welcome :)

---

