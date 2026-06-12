---
title: "Grub and Windows in External HDD"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by patchido on 2009-05-09
well, I've been trying this for a while but i cant, some people already tried to help me out but i just cant work it, here it goes, i own a dell inspiron 1420 with vista installed, i wanted ubuntu but my father was kind of afraid i was going to crash the computer, so i bought an external drive (all this was about 2 years ago) so i installed ubuntu and been using it since then, recently I've been in need of a xp version to play some games, so i got a cd of Windows xp sp2 with SATA drivers and installed it in a partition on my EXT but for evading damaging my INT HDD i took it out and placed my EXT inside and installed and then the drivers. afterwards i restored GRUB and tested it, all went fine all the OS's worked. and when i extracted the EXT and used it as i should with the other HDD in place when i try to load windows it will crash, wont load. It starts loading and i get a milisecond blue screen and REBOOT. so i investigated and found out that windows isnt bootable form a non.primary drive. and then a guy from these forums told me about map command in grub, but i couldnt make it work from what he said. so i am really desperate, i need this to work cause i've been losing too much time and i am becoming mad xD

thx for your time reading this

---

### Post by coffeeaddict22 on 2009-05-09
Hi,
Know the feeling.
You've got a few options.  WINE is pretty good at present, and you could just try to run your games under that.  Another option is VirtualBox, although if its a cutting edge game that'll give you less than perfect performance.
For a triple boot, You're probably best to delete Ubuntu for now, install Windows, and then reinstall Ubuntu.  It is possible to sort out the bootloader after installing Win XP on top of Ubuntu, but it's not fun.  Have a look at the APC article- it's nice and logical.  [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

---

### Post by patchido on 2009-05-09
but the bootloader isnt the problem, it is going into windows but windows crashes, but this doesnt happen if i use my external into internal,

---

