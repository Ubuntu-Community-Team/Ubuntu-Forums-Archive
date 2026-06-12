---
title: "Video problem (i915) with 10.04 on a Latitude D505"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by toothlesrooster on 2011-03-25
Alright.  I'm a complete noob when it comes to anything Linux so bear with me if I get some nomenclature incorrect.  I tried running Redhat for a couple of weeks over 10 years ago but never pursued it because of time and hardware constraints.  That said, I've always wanted to learn to use Linux.  I've got an old Latitude D505 laying around that seems perfect for the job, so I downloaded the latest LTS, 10.04, made a bootable USB flash drive and went to town.  I had problems with it locking on a black screen before it could load.  I couldn't install or run it live from the disk.  Same from a live CD.  I did some Googling and found that if I put "i915.modeset=1" in the Grub command line before booting that I could get it to load Live and the install menu.  Yay!  I partitioned my drive and installed 10.04.  Now it locks on the same screen every time I try to boot.  I'm not Linux savvy enough to know how to get to a command line before it locks or where to go to add this line of code to fix the graphics problem so I can fix this.

I ca re-install Ubuntu, it's not a big deal, but I don't know how to add this string to my boot parameters so it will be permanent and actually boot after I'm done installing.

Like I said.  I'm completely new to this.  I'm not even familiar with logging in as root any more or using sudo.  Any help you could provide would be awesome!  Thanks guys.

Gavin

---

### Post by wojox on 2011-03-25
Two ways to do this. 

First try holding down the left shift key after you boot and see it it brings you to a prompt to edit your kernel line.

Second boot a live cd again, like when you installed it and edit /boot/grub/grub.cfg and add that to your kernel line then edit /etc/default/grub and add it after "quiet, splash".

---

### Post by toothlesrooster on 2011-03-26
That looks like it may work, but I'm a complete newb.  Inside the grub.cfg file, what's my kernel line?

---

### Post by toothlesrooster on 2011-03-26
It also won't allow me to edit the grub file.  It say's I don't have the permissions necessary to save the file.

---

### Post by Quackers on 2011-03-26
Forget grub.cfg.
Follow the part of the guide below headed
"How to permanently set kernel boot options on an installed OS (not wubi)"

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Don't forget the sudo update-grub afterwards which updates grub.cfg for you :-)

---

