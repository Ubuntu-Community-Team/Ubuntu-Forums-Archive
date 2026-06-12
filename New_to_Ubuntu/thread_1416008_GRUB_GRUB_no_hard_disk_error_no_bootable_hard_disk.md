---
title: "GRUB GRUB no hard disk error no bootable hard disk - insert bootable cd press any key"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by beaver_313 on 2010-02-25
I am using a mac OSX version 5.2 and trying to install ubuntu 9.04 with grub because i tried instling 9.10 and grub2 wasnt working for me now it says GRUB GRUB hard disk error no bootable device insert bootable cd and press any key it freezes at this screen. I have split the mac partition deleted the FAT32 format and installed ubuntu onto that partition and i downloaded grub to sda3 and did all that like im supposed to but when i try to boot the linux os that grub screen pops up and i have to hard shut down my computer. Any ideas? I couldnt find any other threads on this.

---

### Post by ubunterooster on 2010-02-25
ppc architecture?

---

### Post by beaver_313 on 2010-02-25
Sorry im really new to this and i dont know what any of that means but i tried all of those and they all say couldnt find package. Anything else?

---

### Post by ubunterooster on 2010-02-25
are you using a ppc or intel cpu?
in the terminal enter: sudo uname -a
what's it say back?

---

### Post by beaver_313 on 2010-02-25
um intel i believe.
It says Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by ubunterooster on 2010-02-25
i386 or x86_64?
I'd reccomend using RescueCD to reinstall grub

---

### Post by beaver_313 on 2010-02-25
i686 so i guess thats ppc? Ok ill try that.

---

### Post by ubunterooster on 2010-02-25
i686 is sixth-gen x86. so I assume you are using 64bit.
  SystemRescueCD: [http://sysresccd.org](http://sysresccd.org)  is a verry important tool to have.

---

### Post by beaver_313 on 2010-02-25
Ok so that didnt work it said it couldnt find the linux image. So im trying to reinstall linux again and then grub.

---

### Post by beaver_313 on 2010-02-25
I think maybe the problem is that my linux partition isnt mounted? Because on the mac osx it says under disk utilities that it and linux swap neither are mounted but it also wont let me mount them.

---

### Post by ubunterooster on 2010-02-25
I doubt it would be easy, if possible, to mount Linux from INSIDE mac's OS

---

