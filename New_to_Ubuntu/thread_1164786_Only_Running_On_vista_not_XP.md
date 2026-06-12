---
title: "Only Running On vista not XP"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Laurence94 on 2009-05-20
So i am running Ubuntu off an external hard drive i installed it through a computer with a friend it works fine, but when i try and run it on XP's it doesn't work it only runs on vista. the grub fails to load on xp. i am new to ubuntu. does this have to do that i installed it through a vista computer or does it have to do with my external drive?

---

### Post by nhasian on 2009-05-20
thats odd.  if your booting off the external drive it shouldnt matter what OS is installed on the internal drive.  as a matter of fact, you can boot from the external drive even if no hard disk was present inside the computer.

I recommend checking the bios settings to see if there are any bootup options like maybe change it to boot from USB-FDD to USB-HDD or something like that.

---

### Post by Laurence94 on 2009-05-20
well i go to the boot menu and change to priorities to my HDD drive but it is not like the vista one and no tutorials will help me solve the problem. but it only runs on vista.... it has a grub loading error in exp. and my XP computer has a better graphics card and i can more effects and us more of the mother board memory instead of just the hard drive memory. It is a problem to run it only on my vista because it is hell it freezes up after when i try boot vista. and it overheats every few hours so big dowloads will be hard. a link to a tutorial would help.

---

### Post by linux_votary on 2009-05-20
Could you tell the grub error that you get? And the BIOS does not depend on the OS you use whether Vista or Xp...

---

### Post by Laurence94 on 2009-05-20
ill try now and write it now ok?

---

### Post by Laurence94 on 2009-05-20
i changed the boot prioreties to my drive and so on and it didnt even try and boot from it! it went striaght to exp!!!!!! and when i went on to Xp to write this on my computer only one of my exterbal drives partitions are there! the one without ubuntu. maybe my usb port is screwed or sumfing but it only read onb partition!!!! and its th wrong one

---

### Post by Laurence94 on 2009-05-20
i just booted my vista with the drive everything works perfect o0n ubuntu...

---

### Post by YldGuy on 2009-05-20
> So i am running Ubuntu off an external hard drive i installed it through a computer with a friend it works fine, but when i try and run it on XP's it doesn't work it only runs on vista. the grub fails to load on xp. i am new to ubuntu. does this have to do that i installed it through a vista computer or does it have to do with my external drive?

Is it installed on the external harddisk or have you done the USB install?

> well i go to the boot menu and change to priorities to my HDD drive but it is not like the vista one and no tutorials will help me solve the problem. but it only runs on vista.... it has a grub loading error in exp. and my XP computer has a better graphics card and i can more effects and us more of the mother board memory instead of just the hard drive memory. It is a problem to run it only on my vista because it is hell it freezes up after when i try boot vista. and it overheats every few hours so big dowloads will be hard. a link to a tutorial would help.

As i gather, this XP and Vista machine are different. And Ubuntu was installed using the Vista machine on that external USB HDD. When you tried to boot off the USB HDD you got a GRUB error. Its because the GRUB entry must have the harddisk no: different to that when you use XP.

> i changed the boot prioreties to my drive and so on and it didnt even try and boot from it! it went striaght to exp!!!!!! and when i went on to Xp to write this on my computer only one of my exterbal drives partitions are there! the one without ubuntu. maybe my usb port is screwed or sumfing but it only read onb partition!!!! and its th wrong 
one

Your USB drive is not screwed. Its because the filesystem is different in linux. Windows cannot read it natively. You need to use ext2fs to read linux partitions in windows.


My guess is that since you installed using the Vista machine, the GRUB takes the harddsik number it was alloted earlier and it cannot find that same number with XP. I would suggest getting the GRUB entry from your USB harddisk and change the relevant values for the harddisk while it is connected to XP machine.

---

### Post by Laurence94 on 2009-05-20
I am using an external drive
it is installed onto a partition on the drive
ok what do you mean by hard disk entry? and number........and relevnt values...
i am a noob plaease explain

---

### Post by YldGuy on 2009-05-20
> I am using an external drive
it is installed onto a partition on the drive
ok what do you mean by hard disk entry? and number........and relevnt values...
i am a noob plaease explain


The boot sequence that you see with VIsta is in /boot/grub/menu.lst. It means in your Ubuntu filesystem (which is identified as /) there is a boot folder. Within the boot folder there is a grub folder and within that the grub entries are listed in menu.lst. The menu.lst has all the information that is required to boot from a particular harddisk or partition.

When the Vista is connected do this:
go to ubuntu, open the terminal and type the following -

sudo fdisk -l
cat /boot/grub/menu.lst

that will give you the grub entries + the partition layout. post the contents here.

Now with the XP connected boot off from the Ubuntu live CD and type 
fdisk -l

post the contents of this also here.

---

### Post by Mark Phelps on 2009-05-20
Are you sure that your XP machine provides the BIOS option of booting from an external drive thrugh USB?  

I'm only asking because the newer Vista-preloaded machines generally DO provide this option, while the older XP-preloaded machines do not.  

If there is no option in your XP machine to boot from USB, there's nothing you can do to make this work (unless there is a BIOS upgrade that will add this option).

---

