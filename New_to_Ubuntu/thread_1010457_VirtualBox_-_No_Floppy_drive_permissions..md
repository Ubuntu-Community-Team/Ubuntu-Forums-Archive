---
title: "VirtualBox - No Floppy drive permissions."
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-12-13
Hi,

I installed VirtualBox and when I start a virtual machine I get the following problem:


> Cannot open host device '/dev/fd0' for read/write access. Check the permissions of that device ('/bin/ls -l /dev/fd0'): Most probably you need to be member of the device group. Make sure that you logout/login after changing the group settings of the current user.

VBox status code: -38 (VERR_ACCESS_DENIED).

I know 8.10 decided to drop floppy drives, so in order to use mine I added the line "floppy" to the file /etc/modules 

So basically I need to fix this so that virtual machine can access my floppy drive.

If anyone can advise me on how to fix this, then thanks will be given.

Thanks!

---

### Post by Swerve1000 on 2008-12-14
Is it not possible to use a floppy disk with 8.10 now?

Seems they have been removed from the distro.

If what I'm trying to do is impossible please do tell me as I'm still trying to figure this out.

---

### Post by howefield on 2008-12-14
I didn't know that Ubuntu couldn't use floppy drives out of the box anymore. How things move. :)

Anyway, it might be possible to use your floppy drive by following these instructions. I don't have a floppy to try them, so can't give you a gaurantee or further help, but it might give you a starting place. Taken from another forum (knudfl).


------------------------------------------------------------------
Ubuntu 8.10 : Yes, you are right, the ubuntu guys probably think :
No floppy users anymore !

It is possible to do, and what I am showing you now,
probably will have a much easier solution :

1) 'sudo modprobe floppy'
(if any doubt, do 'lsmod | grep floppy'

2) 'sudo mkdir /mnt/floppy'

3) 'ls /dev | grep fd0' and if no "fd0"
do 'cd /dev' and ' sudo MAKEDEV fd0'

4) add this line to /etc/fstab :
/dev/fd0 /mnt/floppy auto user,exec,rw,noauto 0 0

5) 'sudo mount /mnt/floppy'

6) go to /mnt/floppy in the file manager to watch files.

---

### Post by Swerve1000 on 2008-12-14
Hi howefield, thanks for the help buddy :)

I previously in order to use the floppy drive added the line "floppy" to the file /etc/modules

Should I now remove this in order to use the method you have listed?

I really don't want to have to reformat my machine again if this goes wrong. Will the floppy drive now auto mount using this method and just 'work' like the cd drives do?

I'm being extra careful because twice I've had to reformat this weekend due to errors I've made trying to fix thing.

---

### Post by howefield on 2008-12-14
No probs, if it were me, I'd put the install back the way it was, ie, remove the line in modules that you added. I don't use a floppy drive so can't talk with authority, just wanted to give you a start.

Should also point out that you might want to look at an imaging program, which you can use to take an image of your disk, so the pain of reinstalling is gone. I use true image from Acronis, it is a commercial prog, but there are many free alternatives.

---

### Post by lkraemer on 2008-12-15
Sverve1000,
Just remember that the FLOPPY in the VirtualBox menu is the Physical
IDE Floppy attached to the Motherboard Port and not a USB Externally attached USB Floppy.  

If you are using a USB External Floppy, or care to use one, just ENABLE
USB 2.0 Support, then Add a NEW Filter, and if you are running the NON OSE
Version of VirtualBox you should be able to Right Click on the USB Icon
in the lower Right Menu to Enable the Floppy when it is Plugged in.
It works fine.

lk

---

