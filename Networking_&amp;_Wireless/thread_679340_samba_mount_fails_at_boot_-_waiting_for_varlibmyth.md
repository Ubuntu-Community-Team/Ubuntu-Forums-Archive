---
title: "samba mount fails at boot - waiting for /var/lib/mythtv/videos"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by sonic6567 on 2008-01-26
Hello,

Mythbuntu (ubuntu 7.10)

I have a master system with a samba server share setup that shares the folder /var/lib/mythtv/videos as [videos]

I have a second system that I want to mount that folder.

I edited the /etc/fstab and entered:
//mythtv/videos /var/lib/mythtv/videos  smbfs   credentials=/etc/samba/user,rw,uid=username 0   0

i reboot the second system and... when it is done booting... everything works perfectly.

The problem is that in the middle of the boot process, the system stalls with the message:
waiting for /var/lib/mythtv/videos
And after many many minutes ultimates says:
failed

This long long delay durring boot up is bad.

Any thoughts?

Ben

---

### Post by usererror on 2008-02-17
have you resolved this?

I have the exact same problem.

the odd thing though is that even says it says "Failed" I can still browse to the and everything plays from the share just fine!

SOLVED

I found a resolution to the problem.

Instead of having fstab mount the samba shares from the server to /var/lib/mythtv/videos  I created a folder in home folder of the user my mythtvfrontend runs from:

/home/mediacenter2/videos   fstab mounts to this home folder location.  Then I rebooted and the samba mounts did not fail!  I then made /var/lib/mythtv/videos a symlink to /home/mediacenter2/videos

it works great. I don't know why smbmount will not mount to the /var location.  but this works and I am happy!

---

### Post by cenwesi on 2008-02-21
Try this guys

//192.168.1.xxx/m1 /mnt/movies1 cifs user,credentials=/root/.credentials,file_mode=0777,dir_mode=0777  0 0

---

### Post by sonic6567 on 2008-02-21
The mounting to a home folder then linking the /var/lib/mythtv/video directory to it worked great!  Good idea for a work around.

I'm still wondering about the actual problem though.

I don't see how the changed line for fstab will make a difference as it is still mounting to a directory other than /var/lib/mythtv/videos.

I will try it tonight and see what happens.

Thanks

---

