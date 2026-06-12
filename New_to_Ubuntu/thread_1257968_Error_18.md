---
title: "Error 18"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by mclear on 2009-09-04
New to Ubuntu, will like to try it out. I have two HD's (250GB & 20GB) on a Sony Vaio desktop. Reformated both drives (used to have WinXP). This machine is about 8 years old. Burned the Ubuntu ISO image to a CD, inserted into CD-ROM clicked "Install Ubuntu", use the whole Drive (I believe it went under the 250GB drive) as an option, took the CD out, restared and got "GRUB Loading, Error 18". Reformated again, reinstall and same error message. Went through the forums to find fixes and there's many of them, I'm just not efficient on the terminal window or with command-lines. I'm pretty much a "click" and go kind of person.
Any help will be greatly appreciated
mclear

---

### Post by oldos2er on 2009-09-04
Maybe this will help: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

 You might want to look into updating your BIOS.

---

### Post by halitech on 2009-09-04
if there is no BIOS update, a workaround would be to manually partition your drive and for the first partition, create a 500meg /boot partition, then your / partition (about 15gig) then the remaining for /home. This will put the boot info in the first part of the drive and should resolve the issue (I had the same problem when using a 160gig drive on an old P4 that gave me the same error and creating a /boot partition resolved it)

edit: don't forget about a swap partition as well of about the same as what you have ram

---

### Post by egalvan on 2009-09-04
> **mclear said:**
> I have two HD's (250GB & 20GB) on a Sony Vaio desktop. Reformated both drives (used to have WinXP). This machine is about 8 years old
mclear

Error 18 usually refers to hard drives being too large for the BIOS.

Note... Sony *may* have a BIOS update, check their website.

I would recommend installing the drives so that the 20gb (smaller) is the first (drive C: in Microsoft-speak) or Primary Master.

The 250gb can then be any drive.

Install Ubuntu to the first drive, which is called sda in *nix-speak.
You can setup your '/home' directory on the larger second drive...
and use the extra space for storage.

I would also suggest wiping the drives before starting any other installation, to be sure that any Boot Record stuff is wiped.

Note... Windows "format" is not sufficient for this.

Darik's Boot and Nuke is excellent for this...

[www.dban.org](www.dban.org)


**n.b.**
if your machine is so old that even the 20gb is too large,
then you should use the method 'hailtech' gives (post #3)...
make a separate '/boot' partition at the start of the drive.

---

### Post by mclear on 2009-09-04
That's exactly what I used on the original wiped , used Darik's Boot and Nuke. Will nuke it again and start from scratch with the ideas given on the 3 posts. Thanks you!!

---

### Post by egalvan on 2009-09-04
OK, and let us know if you succeed, and how you succeeded...
this will help others, it you share.

---

### Post by halitech on 2009-09-04
if the machine is old enough that even the 20gig won't work without the /boot partition, it might be time to retire the machine :)

you could still do manual partitioning and use the 20gig for / and swap and then load /home on the 250gig.

---

### Post by LewRockwell on 2009-09-04
> **egalvan said:**
> OK, and let us know if you succeed, and how you succeeded...
this will help others, it you share.

+ 1

not only that...but it would help others even more if they know your equipment specifications

.

---

