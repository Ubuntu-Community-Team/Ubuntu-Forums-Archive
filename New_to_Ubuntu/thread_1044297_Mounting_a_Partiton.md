---
title: "Mounting a Partiton"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by oopsie on 2009-01-19
Hiya!

I installed Ubuntu a few weeks back to test it. But I gave it the bare minimum amount of disk space I could, because I was just testing.

Well now it's full.

I was thinking of deleting Ubuntu and reinstalling it with more room. But, I thought that's probably a bit drastic.

So, I repartitioned a drive so there is 50GB of free space, and I'm trying to give that space to Ubunutu, but I'm not quite sure how to do it.

I'm 99% sure I've partitioned it right. and 80% sure I formatted it right. I don't seem to have killed any of my old Windows stuff. But, I'm not sure how to make this 50GB accessible from in Ubuntu

Can anyone offer some advice?

Thank you in advance

---

### Post by emarkd on 2009-01-19
If you're looking for a graphical tool, I've always had good luck with gparted.  It's in the repositories if you don't have it.

---

### Post by Oak37 on 2009-01-19
Hello,

When you created the partition did you format it as ext3? Any of the partitions should be seen by clicking Places in the menu bar and scrolling down to Computer.

---

### Post by oopsie on 2009-01-19
> **Oak37 said:**
> Hello,

When you created the partition did you format it as ext3? Any of the partitions should be seen by clicking Places in the menu bar and scrolling down to Computer.

Yes, I did format it as ext3. And I can actually see a 50GB thing in the places list. And I can click on in and says it's mounted

But, if I right click in it to make a new folder or anything, I can't seem to do anything. and there's a folder already there that says "Lost+found", but if I click on that it errors and says the contents cannot be displayed.

I'm guessing I've messed up somewhere again.

---

### Post by theozzlives on 2009-01-19
you could use System>Administration>Partition Editor off the live CD and just make your Ubuntu partition bigger.

---

### Post by oopsie on 2009-01-19
> **theozzlives said:**
> you could use System>Administration>Partition Editor off the live CD and just make your Ubuntu partition bigger.

No, that drive's full. The new 50GB is on a different drive.

---

### Post by emarkd on 2009-01-19
Are you trying to extend your existing partition into that space?  If so, you could use lvm.  Search around for a how-to.  It's not hard and there's some good tutorials out there somewhere.

---

### Post by oopsie on 2009-01-19
> **emarkd said:**
> Are you trying to extend your existing partition into that space?  If so, you could use lvm.  Search around for a how-to.  It's not hard and there's some good tutorials out there somewhere.

No, the drive I have Ubuntu on is virtually full with stuff. There's very little room to expand any partition in there. I'm trying to give Ubunutu 50GB from a different drive.

---

### Post by -kg- on 2009-01-19
I'm not sure, but isn't oopsie going to have to "chown" the partition?  I'm relatively new to Linux myself.

---

### Post by emarkd on 2009-01-19
lvm doesn't require that the spaces be on the same physical drive.  i've got a media server with three disk drives in it, but it appears as though it's got about 2 TB of storage on one very large disk because of lvm.

if you just need access to the space and it doesn't have to appear contiguous, you can just mount it somewhere.  in fact, ubuntu may have done it for you.  what does

```
mount
```

tell you?

---

### Post by oopsie on 2009-01-19
/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/me/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=me)
/dev/sdc5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by phantom@atom-desk on 2009-01-19
Is'nt it possible to move whole of the home folder on that other physical drive? I think it should be

---

