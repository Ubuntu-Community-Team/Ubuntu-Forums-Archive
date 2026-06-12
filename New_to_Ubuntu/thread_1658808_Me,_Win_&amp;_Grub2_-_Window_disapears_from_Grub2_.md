---
title: "Me, Win &amp; Grub2 - Window disapears from Grub2 on Update"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by DENSA on 2011-01-03
[LIST=1]
[*]I decided to try my hand at learning a little about Linux so I wiped my HDD and installed a fresh copy of Win 7 x64 followed by the latest version of Ubuntu 10.10 (32 bit) with no problems. Ubuntu prompted me to install updates which I did and lost the link in Grub2 to Windows. I updated the windows Mbr and got access back to windows but lost Grub, then installed Grub again and lost windows. I installed both OS again and then installed Setup Manager to change the boot order but yet again no sign of windows in the dropdown or the boot screen. I feel like I am going round in circles and wondered if anyone could point me in the right direction.
[/LIST]

---

### Post by theozzlives on 2011-01-03
> **DENSA said:**
> [LIST=1]
[*]I decided to try my hand at learning a little about Linux so I wiped my HDD and installed a fresh copy of Win 7 x64 followed by the latest version of Ubuntu 10.10 (32 bit) with no problems. Ubuntu prompted me to install updates which I did and lost the link in Grub2 to Windows. I updated the windows Mbr and got access back to windows but lost Grub, then installed Grub again and lost windows. I installed both OS again and then installed Setup Manager to change the boot order but yet again no sign of windows in the dropdown or the boot screen. I feel like I am going round in circles and wondered if anyone could point me in the right direction.
[/LIST]

Have you tried
```
sudo update-grub
```

---

### Post by DENSA on 2011-01-03
Thanks Ozz but I tried that and it still doesn't recognise windows, I tried to follow as many guides online before I posted her., I was wondering if it could be a conflict between a windows 64 bit os and a linux 32 bit os? I have no idea just a thought.

---

### Post by coffeecat on 2011-01-03
A 64-bit system on one partition and a 32-bit on another won't be a problem.

Check this, a rather unusual situation that has been reported a couple of times. Open either System > Administration > Synaptic or Software Centre and see if os-prober is installed. It comes with a default install of Ubuntu and is responsible for detecting other operating systems for grub, but on occasion it seems to go walkabout after a system update, or disappears for some other reason. All very curious - I don't know why.

If it's not installed, install it and then run 'sudo update-grub' again.

---

