---
title: "After upgrade to 10.10 cannot mount blank  DVD/CD"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by Shallodarns on 2011-06-04
I just came back from a long trip and ugpraded to 10.10. Everything worked fine until I wanted to burn a CD. I can't mount blank DVD or CD's.

I tried to mount it via Console and get the follwing output:

simon@simon-laptop:~$ sudo mount /dev/sr0
[sudo] password for simon: 
mount: /dev/sr0 already mounted or /media/cdrom busy


I also tried it with ~$ sudo mount /media/cdrom but with the same effect.

I then had a look in the fstab file which looks like this:

proc            /proc           proc    defaults        0       0
UUID=810d99d6-94b3-499b-8a3c-6e3fd6b393b8 /               ext3    relatime,errors=remount-ro 0       1
UUID=53109ea6-f984-4fc3-8cde-eb69b6812ce2 none            swap    sw              0       0
/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
/dev/sr0  /media/cdrom  udf,iso9660  user,auto,exec,utf8  0  0

As I am a relative Linux newbie I am not sure if the fstab file is correct, can someone help me out?

---

### Post by cariboo on 2011-06-05
You should need the automount /dev/sr0 line in /etc/fstab any more. Comment it out by putting a # at the start of the line, and try again. Automounting is now handled by nautilus.

---

