---
title: "White screen upon attempt to mount /home at boot"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-03-28
Hi, all:

I'm rebuilding my machine; something about upgrading from KDE 4.1 to 4.2 caused some issues with browser crashes, stuff like that.

I'm getting a white screen error when I try to mount /home at boot.  I can mount a second drive with no problems by editing fstab and temporarily mounting that partition to change permissions and ownership.  It's only mounting the /home partition that causes issues.

Here's the two entries in my fstab:

# /dev/sda1
# UUID=1e5b19dc-a494-40f2-8e80-991942221e84 /home           ext3    relatime        0       2
/dev/sdb1 /media/secondDrive ext3 nodev,nosuid 0 2

I can boot and that second hard drive mounts just fine to the /media/secondDrive directory I created.  Unfortunately, if I remove the hash from in front of the /home line, and attempt to reboot so that all my program files will load, I get a white screen after the splash.

If I remove the hash and use "sudo mount -a" to mount both drives, they both mount fine.  Upon reboot, though...I still get the WSOD.

What could I be doing wrong?

---

### Post by tarahmarie on 2009-03-28
Ah...JIC anyone else has this problem, /home mounted fine after I finished the upgrade to 4.2.  I imagine it had something to do with conflicting .kde directories or something.

---

