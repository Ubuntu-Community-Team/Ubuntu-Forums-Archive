---
title: "Clean-up"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Mark Lee on 2010-11-13
I installated Ubuntu version 10.10 on an 8 gigabyte USB stick with a current persistent memory of 4 gig. During the bootup of ech session a flash screen appears asking if I wish to install or simply test the software. How do I PERMANENTLY disable this screen? Any deletion of the desktop's installion icon is not remembered session to session. Also, the installation includes a copy of WUBI.exe - is there a reason why I cannot delete it? Thanks for your help
                                 - Mark Lee

---

### Post by Monotoko on 2010-11-13
Mark,

A better option may be to insert a Ubuntu installation disk, then install it to the USB. This will create a "permanent" installation that you are after.

---

### Post by wojox on 2010-11-13
I've always had luck with [UNetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by oldfred on 2010-11-13
Some examples of full installs:

Standard full install to flash or SSD:

See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by Mark Lee on 2010-11-14
Thanks all for the replies. Currently, I am not at my own installation, but once I return I plan to implement one of your solutions. Unfortunately, UNetbootin will not be one of them. UNetbootin for Windows does not address persistent memory settings (of which I am aware) USB Universal, however, does. A persistent memory is a "must have" for the work that I intend to do. I like UNetbootin, but unfortunately using it only left me with a redundant startup UNetbootin install/trial menu like the one which I am trying to escape. I have been wondering, though, that if I delete the WUBI.exe file if I would remove the start up menu. Any thoughts? Thanks again.
                                - Mark Lee

---

### Post by Mark Lee on 2010-11-18
[SIZE=3]The solution that worked was provided to me by the Universal USB[/SIZE][SIZE=3] folks and was to edit the syslinux/syslinux.cfg file with a text editor and removing the following:

 [/SIZE][FONT=Arial Black][SIZE=3]ui gfxboot bootlogo [/SIZE][/FONT]

[SIZE=3]Thanks for the help.
                                         - Mark Lee[/SIZE]

---

