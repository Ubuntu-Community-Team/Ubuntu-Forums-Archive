---
title: "Reinstall Windows 7 while Ubuntu and Win7 already installed"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by rez182 on 2011-04-07
basically i had win7 and then created a separate partition for ubuntu and installed ubuntu. so i have both at the moment. but after upgrading the BIOS my win7 is not working. a blue screen of death comes and i cannot use win7 anymore. so is it ok if i reinstall win7 with a DVD or bootable USB?

---

### Post by Elfy on 2011-04-07
Reinstall windows, make sure it works then reinstall grub. Looks worse than it is :)

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by searchfgold6789 on 2011-04-07
Yes, but you will have to reinstall GRUB to your hard disk and update it as well. ```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by rez182 on 2011-04-07
is it like if i reinstall windows 7 now, my ubuntu will be hampered and ill have to install grub to get my ubuntu back working properly?

will my windows 7 be hampered if i reinstall it now?

---

### Post by Elfy on 2011-04-07
No idea about windows. Once you reinstall windows it will install it's bootloader and ubuntu will not be on it.

Hence the need to reinstall grub.

---

### Post by seawolf167 on 2011-04-07
See [here ]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")- "Installing Windows after Ubuntu" and see if that helps at all.

---

### Post by rez182 on 2011-04-07
ill need a second pc to read all the instruction n follow...which i don have at the moment...plus i tried installin windows 7. they dont let me upgrade without changing the files from boot. they tell me to run the upgrade from inside windows 7 normal startup... im screwed...

---

### Post by eriktheblu on 2011-04-07
You might try the Win7 recovery disk.

Sounds like you have an upgrade rather than an install version. If you originally had XP or Vista, you will need to reinstall that before you use your 7 disk (proprietary OSs are funny like that)

Whatever your solution, have an Ubuntu live disk handy to correct your MBR. MS refuses to acknowledge the existence of other operating systems.

---

### Post by rez182 on 2011-04-07
> **eriktheblu said:**
> You might try the Win7 recovery disk.

Sounds like you have an upgrade rather than an install version. If you originally had XP or Vista, you will need to reinstall that before you use your 7 disk (proprietary OSs are funny like that)

Whatever your solution, have an Ubuntu live disk handy to correct your MBR. MS refuses to acknowledge the existence of other operating systems.
my brain cant take it anymore...ill jus sacrifice the current win7 n do a fresh install...wouldent need win7 if my ubuntu could work fine in battery mode with wifi on. it freezes if the wifi is on in battery mode.. sucks i know... n nobody seems to know why n cant help me...

---

### Post by rez182 on 2011-04-18
sorry for the late reply....but i did it...a fresh windows reinstall...with grub2 reinstalled as well....thanks alot everyone...it was a great help...

i used:
[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)
simple and effective...

there are alot of methods out there, which not only didnt work for me, but were very critical too..

---

