---
title: "Messed up big time"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by SpawnCrash on 2010-11-20
I installed ubuntu a while back, on a partition on a different drive. Not my c:/ anyway. I recently reformated my computer and delted the other drives with my ubuntu on because I forgot and thought it was on my c: drive. When I formatted my computer it got half way through and restarted and it when to the grub bootmenu, but it never had boot to: etc it had grub loading error: no such partition. So I thought I'd download win 7 to see if this would fix it but it comes up with a blinking cursor for about 1 minute then goes straight to the grub menu error.


I'm not going to use win 7 just wanted to install it so I could re install ubuntu. But I don't have any disks or usb only the win 7 cod that's why I have to use win 7. How can I get it to boot to my cd? and fix this error?

---

### Post by ubunwhat on 2010-11-20
When you first boot up you need to slip into the BIOS menu before it ever gets to thinking about GRUB.  It will usually flash this on the screen just as you power up.  On most machines it is the F2 key, but it does vary.  Once into the BIOS menu you can change the boot order so that the CD drive is booted prior to the HDD, which would boot to your CD first.  The odd thing is that most machines are set to boot to CD first by default.  If yours is already set to boot to CD and it is not doing so then the CD is not bootable and you are back at square 1.

---

### Post by cchhrriiss121212 on 2010-11-20
You don't need to use Windows if you want to install Ubuntu, you just need an Ubuntu live CD which you must have otherwise you could not have installed it in the first place.

When you boot from the Ubuntu Live CD just select "use whole drive" and it will format the disk and install Ubuntu.

---

### Post by ubunwhat on 2010-11-20
It doesn't really matter at this point if he has a Ubuntu CD.  The machine is not booting to the optical drive anyway, assume he actually does have a Windows CD in the drive.  Having a Ubuntu CD in the drive would not change anything if the default first boot is to the HDD.  This is why machines are set to boot optical first.

---

### Post by SpawnCrash on 2010-11-20
I think I mounted the iso if I can remember correctly. Not too sure, I'll check for the cd I have lots.

---

