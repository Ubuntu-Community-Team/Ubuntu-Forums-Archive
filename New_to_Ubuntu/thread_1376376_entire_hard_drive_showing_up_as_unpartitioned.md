---
title: "entire hard drive showing up as unpartitioned?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2010-01-09
Okay, so I notice on the Palimpsest Disk Utility that there is some unallocated space on my hard drive, but am confused because there shouldn't be. So then I download Gparted to see what my partitions are looking like. According to Gparted, my entire 160 gig hard drive is unallocated space. It didn't recognize anything. What's going on???

I've also had some problems at boot time lately? Would this be the cause? About 1 in 5 times grub doesn't load my OS, it says that initramfs timed out and then I have to restart the machine.

---

### Post by Captain_tux on 2010-01-09
Assuming you're in Linux now, post the results of **df -h**...

---

### Post by b0b138 on 2010-01-09
Whats interesting isn't that it's showing unallocated space (with palimpest), but that its showing 18446744071 GB of unallocated space. 

In a nutshell your entire partition table is corrupted. It would be a good idea to backup what you need to to something else. From there you can see if fsck will straigten it out. If not the whole drive needs to be reformatted.

Or since it's also saying there are many bad sectors, the drive might be on its last leg

---

### Post by warfacegod on 2010-01-09
What's really interesting is that I read a thread with an issue I and others have never seen. Then I find another. And now this one. All with very similar problems.


Hope this puts you on the path:

[http://ubuntuforums.org/showthread.php?t=1366233&highlight=partition+table+repair]("http://ubuntuforums.org/showthread.php?t=1366233&highlight=partition+table+repair")

---

### Post by jimmybarcelona on 2010-01-10
> **Captain_tux said:**
> Assuming you're in Linux now, post the results of **df -h**...

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              45G   21G   22G  49% /
udev                 1007M  312K 1006M   1% /dev
none                 1007M  188K 1006M   1% /dev/shm
none                 1007M  200K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/home/coryellcp/.Private
                       45G   21G   22G  49% /home/coryellcp/Private

```

---

### Post by jimmybarcelona on 2010-01-10
well, before bed tonight think i'll back everything up and see if fsck will find/fix errors in the partition table. if that doesn't work, reformatting and reinstalling from a backup isn't too hard. I'll let you know how fsck turns out.

---

### Post by jimmybarcelona on 2010-01-11
I booted from the live CD and having problems running fsck. Some of those partitions don't even exist anymore, and I tried running "fsck -A" but it didn't actually run anything, it just spit out "fsck from util-linux-ng 2.16". I think i know what happened though. Palimpsest is showing a 104 gig ntfs filesystem. I started out with an ntfs system when I was dual booting windows xp in order to test things out. Then when I liked ubuntu I used my gparted live cd to delete the windows partition and expand the ubuntu partition. Could it be that something went wrong there? How do I fix a non-existent file system? Is is just time for a clean install? will that fix the partition table?

---

### Post by warfacegod on 2010-01-11
It will as long as you reformat the entire drive. Seems a bit drastic though.

---

