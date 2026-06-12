---
title: "Regaining GRUB !!"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by vamsi_spr on 2011-01-23
Hello guys , i got Windows7 and UBUNTU installed in my lappy , now i wanted to re-install windows7 due to the clutter , now i fear that i would lose the GRUB loader list if i do that coz it happened with me with the Windows XP earlier ...is there anyway i could regain the GRUB after i re-install windows ??

---

### Post by Elfy on 2011-01-23
Once you've reinstalled windows - reinstall grub with a livecd/usb 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by vamsi_spr on 2011-01-23
can anyone put it short and lucid ??

---

### Post by Rubi1200 on 2011-01-23
The link forestpiskie provided is the easiest and simplest method of reinstalling GRUB.

If you are not sure what to do, I suggest you install Windows and then run the boot info script linked at the bottom of my post.

We will then walk you through the procedure.

---

### Post by alaukikyo on 2011-01-23
A easy GUI way is to Download [this]("http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/pool/main/g/grub-customizer/grub-customizer_2.1-0ubuntu1%7Eppa1m_i386.deb")  and install it on the livecd and then go to Applications -> System  Tools -> Grub Customizer and then File -> Install to MBR.

---

### Post by vamsi_spr on 2011-01-23
Thnk u guys i followed the steps in the link and i could regain the GRUB but i have few questions 

1.) How to rename the present drives ..i mean the names are kinda mystic !!

2.)Is there any facility of address bar in UBUNTU  so that i can copy, paste the path ??

---

### Post by alaukikyo on 2011-01-23
> **vamsi_spr said:**
> Thnk u guys i followed the steps in the link and i could regain the GRUB but i have few questions 

1.) How to rename the present drives ..i mean the names are kinda mystic !!

2.)Is there any facility of address bar in UBUNTU  so that i can copy, paste the path ??

1. Right click on the drive and rename it.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181784&stc=1&d=1295791025[/IMG]

2. Ctrl + L

---

### Post by vamsi_spr on 2011-01-23
I already tried renaming in that manner but it says it cannot rename coz "operation not supported by backend"

---

### Post by alaukikyo on 2011-01-24
> **vamsi_spr said:**
> I already tried renaming in that manner but it says it cannot rename coz "operation not supported by backend"

Firstly you need to alt +f2 then type gksu nautilus and then ok 
now unmount the partition that you want to rename and then rename it.

---

