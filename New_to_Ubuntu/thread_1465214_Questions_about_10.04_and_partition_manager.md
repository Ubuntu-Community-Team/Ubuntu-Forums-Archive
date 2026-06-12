---
title: "Questions about 10.04 and partition manager"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by theubersmurf on 2010-04-29
So my current system dual boots with Windows Vista x64, however the installation of Vista has become a bit of a mess with my Koala install (I installed it pretty recently). It still boots, and I did indeed defrag before and after, but I'm thinking of reinstalling both when 10.04 comes out. The problem I think I'm going to have is using the partition manager. The default options listed are pretty nuclear, and The partition manager in (at least in Koala) was a bit over my head, and I had to rely on the default options. Is there anywhere a tutorial on the use of the partition manager in the Ubuntu ISO so that I can set this up the way I want it. Also, I noticed that today is the release date of Lynx, is it in fact released? Or is it still brewing?

---

### Post by PriceChild on 2010-04-29
If you are going to reinstall both of them, (wiping everything you have on the disk) I would suggest that you install Windows first, and ubuntu second.

Check out [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) for a good guide on installing. It is section 8 that has what you are worried about. It even has a cool photo of what you should expect, which looks much nicer than the last time I installed Ubuntu!!
> If you want to install Ubuntu on a single partion Dual Booting,  Select **Guided – resize.** In the New partition size  area, drag the area between the two partitions to create your desired  partition sizes. Click **'Forward**. The Who are you?  window appears.

---

### Post by theubersmurf on 2010-04-29
Ok great, is 10.04 out yet? or is it still in beta atm?

---

### Post by PriceChild on 2010-04-29
Its due today. ubuntu.com will change to say so when it is available.

---

### Post by zeroseven0183 on 2010-04-29
The screenshot in Section 8 is a bit old already. But as PriceChild suggested, you can install Windows first then Ubuntu since Ubuntu can automatically detect the first OS installed on the drive. Be sure you do what is said here [https://help.ubuntu.com/community/WindowsDualBoot%20#Install Ubuntu after Windows](https://help.ubuntu.com/community/WindowsDualBoot%20#Install Ubuntu after Windows)

Hope that adds to the help

---

### Post by ex-wirecutter on 2010-04-29
Just a word of caution , I tried to install Lucid dual boot with Vista and got the error " partition not found " It seems on some PC's gparted has a problem with the Vista partition.

---

### Post by zeroseven0183 on 2010-04-29
> **ex-wirecutter said:**
> Just a word of caution , I tried to install Lucid dual boot with Vista and got the error " partition not found " It seems on some PC's gparted has a problem with the Vista partition.

Can you confirm if Vista is still in the partition table?
If there are available updates in Ubuntu, download and reboot your pc and see if it's fixed.

---

### Post by ex-wirecutter on 2010-04-29
No , I got rid of Vista , but it was originally dual boot with XP and after deletion it left behind the Vista bootloader . This didn't bother me at the time as I just booted to "earlier version" .  However when I installed Lucid side by side , it couldn't seem to re-write the boot options , so neither of them worked . Via google , I found that this had been reported to launchpad and it seemed only a few people had this problem .  After a day or so of trial and error it's sorted now .

---

