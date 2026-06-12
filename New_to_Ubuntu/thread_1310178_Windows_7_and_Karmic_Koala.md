---
title: "Windows 7 and Karmic Koala"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-11-01
I recently installed Ubuntu 9.10 (Karmic Koala) and have been loving it. I had 100 GB partitioned for Vista, but Ubuntu was by primary OS; however, it would give me an option of which OS to boot on my computers start-up, then default to Karmic after 10 seconds. I installed Windows 7 today and wrote it over my Vista partition. Windows 7 only recognizes the amount of space that I had for vista so I know it didnt write over Karmic. But now when I boot my laptop up, it automatically runs Windows 7, without giving me the option of which to boot. Furthermore, I cant access the files I have on Karmic. I have an HP DV7 laptop if this helps

---

### Post by mikewhatever on 2009-11-01
You'll need to reinstall GRUB2 from the live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by sbrown1992 on 2009-11-01
You may find this guide easier to follow:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Zoot7 on 2009-11-01
> **sbrown1992 said:**
> You may find this guide easier to follow:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
That guide is for Grub 1 - Karmic uses Grub 2.

---

### Post by Captainflowers91 on 2009-11-01
The problem is, I can't get into Ubuntu to to a terminal install. How would I re-install grub 2?

---

### Post by DigitaLink on 2009-11-01
Yes, Microsoft continues to ignore the fact that it's users may very well use more than one OS and merrily wipes out your bootloader when you install Windows.  Isn't that nice of them? 

"It's not a bug, it's a feature."

---

### Post by sbrown1992 on 2009-11-01
@Captain Flowers: You would use the Live CD

---

### Post by Captainflowers91 on 2009-11-01
What? Do you mean re-do the install process? I have some documents on it that I cant risk losing. How would I do this without re-installing the whole OS?

---

### Post by Nburnes on 2009-11-01
You can use an EasyBCD beta to boot into Karmic from Windows bootloader.

---

### Post by mikewhatever on 2009-11-01
> **Captainflowers91 said:**
> The problem is, I can't get into Ubuntu to to a terminal install. How would I re-install grub 2?

> **Captainflowers91 said:**
> What? Do you mean re-do the install process? I have some documents on it that I cant risk losing. How would I do this without re-installing the whole OS?

Please refer to post #2 and follow the guide it links to.
You should also be able to boot Ubuntu, by selecting 'Boot from the hdd' in the Live cd menu.

---

