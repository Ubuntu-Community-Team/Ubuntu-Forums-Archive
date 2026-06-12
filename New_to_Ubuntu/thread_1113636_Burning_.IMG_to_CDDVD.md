---
title: "Burning .IMG to CD/DVD"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by The Irish Blend on 2009-04-01
ok i'm trying MKlinux on my laptop beacuse it looks challanging. i cant get the .img to burn right the disk wont boot all the data is there but no go.

how i burnd the .img on ubuntu... 1. i renamed the disk from .img to .iso
2. i used the ubuntu burning software to burn the disk. it burnd sucessfuly.

after all that i placed the dick in my ubuntu laptop. My laptop bypassed by MKLINUX CD and went right into Ubuntu linux (HDD0).

laptop boot order (f2)
1. CDROM/DVDRW
2. HDD0
3. Floppy 3.5
4. LAN RJ45

Have fun with this one i'm already annoyed. My desktop is ubuntu i love it i like to play with linux distros.

---

### Post by aeiah on 2009-04-01
im not being sarcastic, its a genuine question, but: what made you think changing the filename from .img to .iso would turn it into an iso? maybe it is the same type of file but i always thought they were pretty different.

anyway. you could convert it to .iso with some command line programs, or you could use something that supports .img files. brasero does. perhaps that'll work?

---

### Post by 123456789123456789123456 on 2009-04-01
img, iso, dmg, are all image files.  just made by different programs, .img is a image file made by I think a windows program, dmg is a file format used primarily by macs, iso is generic, used by most operating systems.  mklinux, I am assuming is a distribution of linux that you have the image file for.  Does the cd have the boot folder on it?, just because it is img, instaid of iso should not make a difference on rather or not it is bootable.  also check the program you are useing, this there an option to make the disk bootable.  I would have to look at the files listed on the cd.  can you do a ls-l command on that cd, and send the resulted text?  if I know what files and folders are listed on the disk, I can at least tell you if the disk was originally bootable or not.

---

### Post by llamabr on 2009-04-01
> **aeiah said:**
> im not being sarcastic, its a genuine question, but: what made you think changing the filename from .img to .iso would turn it into an iso? maybe it is the same type of file but i always thought they were pretty different.



Nope.  Just different naming conventions, like .jpg and .jpeg.

---

### Post by The Irish Blend on 2009-04-01
1.Well the weird thing is that the CD Seeks in the tray.

2.The Mklinux website said to convert it to .iso by renaming it.

3.No boot folder, but there is a "Boot.Catalog" and a "Yaboot_0.5"

I only have one more blank CD so i want to be almost/are sure that it will work when i burn it.

I appreciate this a lot btw

---

### Post by 123456789123456789123456 on 2009-04-01
changing the file extention probably will not do any conversion at all, except possible on a windows machine.  do you have a virtual software package of any kind, like vmware, or simular.
easy way to see if the disk was made to be bootable would be to have a virtual machine made, and try to boot from the image.

Tell you what.  I have a copy of vmware.  I will donwload the image file, and see what I can do at my end.  I should be able to tell you what is going on.

---

### Post by llamabr on 2009-04-01
Only one disk left:

I don't know what app you use, but cdrecord from the command line has the --dummy flag that runs the process but doesn't engage the laser, so you can make sure everything runs without actually burning a disk.

---

### Post by cjv8888 on 2009-04-02
I  had trouble burning an .img file whether in Windows or in Ubuntu. So I always change the extension to .iso and the burn always comes up perfect.  Do not know why.
Are they always interchangeable ?

---

### Post by atomizer on 2009-04-02
Qoustion:  is your laptop an apple?

seems you have an ppc image (yaboot is made for Apples)

---

### Post by The Irish Blend on 2009-04-02
-UPdate-

well I made a new mklinux cd using windows (i have a duel boot) and a .img to cd application and it still doesn't boot.

My laptop is a Acer Aspire 3000, That makes since. anyway i can bypass this? or can PPC only Work on ancient macs?

---

### Post by mikechant on 2009-04-02
> or can PPC only Work on ancient macs?

It certainly won't install directly on any 'standard' PC - desktop or laptop - including your.
You can only install an x86 versions (32 bit) (or an x86-64 versions (64 bit) if your processor is 64-bit capable).

You might be able to run a PPC operating system under an emulator if one exists, but if would be very slow as each instruction has to be interpreted, possibly generating 100's of x86 instructions.

---

### Post by atomizer on 2009-04-02
PPC is PowerPC (like G3 G4 G5 and PS3)

so you need and ancient mac or an PS3 gameconsole to boot your cd

---

### Post by aeiah on 2009-04-02
power macs, use a powerpc processor, wheras the new macs, and all pc compatible computers use x86 (32bit) processors (or 64bit ones).

64bit cpus can handle 32bit x86 operating systems but x86 ones cant handle 64bit. niether can handle powerpc (sometimes abbreviated to ppc) architectures and ppc cant handle x86 or x64. i suggest finding a different distro :p what attracted you to mklinux? there are so many linux distros that there's bound to be another one that appeals to you that supports your computer's architecture (probably x86 32bit)

---

### Post by 123456789123456789123456 on 2009-04-02
Problem figured out.  I went to the web site.  This version of Linux was designed for Apple Mac power PC, mortorala chips set.

The chip set of the old macs worked different.  The BIOS accepts different boot commands to boot the machine up than that of a run of the mill PC.  Therefore, a windows, or ubuntu cd designed for a pc will not boot a mac of this time period, and a boot cd designed for the mac will not boot a pc.

---

