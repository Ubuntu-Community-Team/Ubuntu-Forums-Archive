---
title: "grub loader and windows boot loader"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by norbert26 on 2010-01-30
i installed ubuntu 9.10 in a dual boot setup with windows 7 one partition and ubuntu other. when i start up first i get the grub loader with 5 choices. leave it on the top choice and you will boot into ubuntu 9.10. if yu go to the bottom and hit windows you go to the windows bootloader choose between windows and ubuntu. can i cut this back and have just one bootloader OR swap the order and get windows bootloader first ?

---

### Post by Ji Ruo on 2010-01-30
That reads like you have both a dual-boot setup, and you've also installed with WUBI to the Windows 7 partition. Is Ubuntu showing up on Add/Remove Programs inside Windows?

---

### Post by norbert26 on 2010-01-30
No this is not installed in windows. it is a dual boot install each has its own partition. i gave ubuntu 40 GB and et windows 7 have the rest of a 160 GB HDD. I did the run the live CD from windows a few times BEFORE i did the dual boot installation outside of windows . that is where i most likely picked up the extra bootloader.

---

### Post by Ji Ruo on 2010-01-30
Ok, but just to be sure, if you go into Windows and check your C drive, or Add/Remove Programs, Ubuntu is not showing up there?

If it is, you've installed with WUBI as well, and if you remove it there (using Add/Remove Programs) then you'll lose the second menu screen when you choose Windows.

I haven't used GRUB 2, but here is a tutorial for you that should tell you how to choose the default loading option.

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by norbert26 on 2010-01-30
AH HA !!!! i found something n add / remove windows 7 called ubuntu i took it out and got rid of the windows boot loader.

---

### Post by Ji Ruo on 2010-01-30
> **norbert26 said:**
> AH HA !!!! i found something n add / remove windows 7 called ubuntu i took it out and got rid of the windows boot loader.

This is where I get to say I told you so! :p You would have installed with WUBI while you were checking out the disk in Windows. 

That tutorial should help you if you decide you want to change the default OS, and it's an A++ site on both Windows and Linux computing in general.

---

