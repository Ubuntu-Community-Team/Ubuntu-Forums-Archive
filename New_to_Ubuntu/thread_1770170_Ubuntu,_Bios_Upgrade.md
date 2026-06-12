---
title: "Ubuntu, Bios Upgrade"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by MR McD on 2011-05-28
I installed Ubuntu 10.04.1 on a Toshiba Satellite A100, because of a flaky Bios, that causes a password request that even when you know the password it will not accept the password.

I received this unit from my brother, and after searching the Toshiba site found out about the flaky bios. 

I searched the web again and found out how to disable the bios request for a password. But even after that could not get XP to work or access. I had no recovery disk so installed Ubuntu.

After that I went to the Toshiba site and downloaded the new Bios which they state will create a boot disk with the bios on a floppy.

The problem is when I try to copy the download to floppy it says  the file is too large. They have an installation guide which I have downloaded and printed as reference but I find it not helpful.

I have two questions ?

1. Do I have to uninstall Ubuntu to install the bios update, even though the update is supposed to create a boot disk?

2. Is there a way to emulate the floppy file to either CD or a USB stick and try to bypass the floppy route.

These questions may not be appropriate here but if someone could steer me to a possible answer, I would appreciate it. Thanks.

---

### Post by Irihapeti on 2011-05-28
I see that there is a method on the Toshiba website using a USB stick: [http://aps2.toshiba-tro.de/kb0/TSB9902P80000R01.htm](http://aps2.toshiba-tro.de/kb0/TSB9902P80000R01.htm)

There is also a way of updating BIOS using a freedos floppy disk image on a CD. When you've booted from the CD, it "thinks" it's a floppy disk and behaves accordingly.

---

### Post by audiomick on 2011-05-28
To the first question: no you don't have to  un-install Ubuntu. A "boot disk" in the context you are talking about is a tool that will run from the storage medium it is on without having to start the computer  in whatever operating system it has installed. The disk to re-flash you BIOS is, as far as I know, completely independant of any Operating systems that may be installed on the computer. It works on the computer at a level below the operating system.

Just a word to the wise: be careful when flashing your BIOS. If it goes badly wrong, your mother board is junk.


To the second question: I don't believe it makes any difference at all what medium the new BIOS file is on, as long as the computer will boot from whatever drive the medium is in. In other words, it should almost certainly work from a CD, I think, or a USB drive. I must say, though, that I am not sure about this, and could be wrong.

---

### Post by mc4man on 2011-05-28
Whatever it is you downloaded (you could provide a link) - have you tried r. clicking on > extract here?
 And if it does is there a readme and possibly even a <whatever>.iso included in the files?

---

### Post by Mark Phelps on 2011-05-31
I don't know about the Toshiba BIOS updates per se, but I'vwe done BIOS updates on lots of other machines and generally, the BIOS files are either distributed as .bin files or as .exe files.

The first are the actual BIOS files and must use some kind of BIOS updating utility.  And again, they typically require booting into some kind of Windows OS in order to work.

The second are self-extracting archives that MUST be run using MS Windows, and will write themselves into a pre-formatted Diskette.

---

### Post by grahammechanical on 2011-05-31
I have an Asus motherboard and it is true that it comes with a CD that has a utility that lets you update the BIOS in the Windows OS (and so completely useless to me) but it also has another utility that lets you boot from a floppy disc and you get DOS environment. From here you can back up the present BIOS and/or install a new BIOS.

I have never tried this but it seems that you copy an exe file and the BIOS file to the floppy disc. For the record, exe files were DOS programs before Windows was created. I am that old I can remember a time before both Windows and Linux. How sad!

This particular motherboard has a utility built-in to the BIOS that will update the BIOS from a new BIOS file on a FAT32/16 formatted floppy disc.

Does the motherboard manual give any instructions on doing this?

Regard.

---

