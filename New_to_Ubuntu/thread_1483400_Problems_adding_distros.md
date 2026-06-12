---
title: "Problems adding distros"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-05-14
Hi all

I run a netbook which i had previously added windows 7 and osx to (using the chameleon loader) I recently discovered ubuntu (ver 10.04) and added that, as i had read the grub boot loader overwrote the chameleon, but all was fine, ubuntu's loader instantly picked up windows osx and itself on boot... perfect.

My netbook has now been replaced with a newer model (constant buisness commutes limit their 'aesthetically pleasing' lifespan) and so I used it around the home and thought I may aswell use it as a test bed for OS before I mess around with my current nebook (used for work) or my desktop (used for work too sadly!). And thought I'd add a few more OS. I did a bit of research and found that to add pcbsd, i would have to forgo windows xp (fine  i never use it) as it needed a primary partition. all other linux would have to share the extended partitions, but there shouldn't be a problem, just reload grub 2 from ubuntu after.

That was a week ago. I have gone round and round in circles with this one and am starting to think it is not possible. I am trying to configure the hard drive as follows (order on disc)
Windows7 (primary), OS x (primary), [(extended partition) Ubuntu netbook ed,swap partition, linux mint, fedora 12 games spin, data partition for documents (ntfs shared partition), open suse 11.2, swap partition, mandriva one 2010, kubuntu](end of extended partition), pc-bsd (primary partition)

Here's where I'm at - I can install each of them on their designated partitions with no other os on the drive and have them boot fine (instillations are fine) trying to get them all on is a nightmare. At first I tried what was said online - add windows, then osx, then the others in any order (i did this in the order on drive) making sure that a linux with grub 2 is installed last.

I got 'H00000000 hfs+ partition error' from the apple partition and ubuntu had a fit on installation "error 2 installation may fail... and did.

next i tried installing all linux but ubuntu first, without their bootloaders, then pc-bsd without it's bootloader, then windows, osx and finally ubuntu. again ubuntu quit the installation, this time without the error message.

I suspect that the error is being caused by either open suse 11.2 or mandriva one 2010, but i can't be sure (just a hunch).

Obviously as a last resort I'm going to have to keep going through until i find out where the conflict will arise, but this will take an age (9 OS, thats 64 pairings, each with an average set up time (for 2 OS) of say half an hour... I don't have that kind of time!

Has anyone done this? does anyone see where I'm going wrong, can it even be done?!

please help guys!

thanks in advance!

---

### Post by zvacet on 2010-05-15
Why do you push so hard with too many OS on drive.Isn´t is easier to have some of those on Vbox or something similar?

---

### Post by 4Orbs on 2010-05-15
Please take my advice with a grain of salt, but I have two suggestions. First is to forget multibooting with Mandriva, it gave me a load of problems when I tried to multibeoot with it. Second, try using Ubuntu 9.10 rather than 10.04. The older version of grub2 is more forgiving when dealing with multibooting.

I could be wrong.

---

### Post by bennachie on 2010-05-15
@4Orbs

Your advice matches my experience exactly. 

@jonny_j22

If you like the Mandriva style of installation and operation without the hassle, try PCLinuxOS. You will almost certainly find that the "redo MBR" function accessible through the "configurations" menu allows you to get everything booting again, including Ubuntu Lucid.

---

### Post by jonnny_j22 on 2010-05-16
Cheers guys for your suggestions!

zvacet, unfortunatly as i only had a netbook to play with virtualising was kind of out of the question to thoroughly test the OS, but thank you for your help, I would definably consider this on my desktop!

4orbs and bennachie, as expected I can confirm that grub booting mandriva is a pain! Thanks for your advice, fortunately I solved my problems with easybcd. I will create a post about it on here maybe tomorrow for any other newbies that aren't hot on code, but for now, after 7 hours of installing, I'm running away from my pc!

Thanks again guys!

---

