---
title: "My sda2 swap has 2 UUID - ??"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by cat2005 on 2009-10-20
Hi,

My sda2 swap has 2 UUID listed.  How is that possible, and how can I correct it?

**1) Here is my most recent FSTAB, with the portion of interest in bold:**

 / was on /dev/sda1 during installation
UUID=53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=14e6c3ab-a70a-461e-a35d-92795fabe5a8 /home           ext3    relatime        0       2
[B]# swap was on /dev/sda2 during installation
UUID=cf64d36c-05c4-4e69-a01f-5c1818a366d4 none            swap    sw              0       0[/B]
UUID=90272743-8704-454a-986c-e7cd45dfa8f /media/sda4 ext3 sync,noauto,rw,user 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


**2) Here is:   ls /dev/disk/by-uuid -lah**

lrwxrwxrwx 1 root root  10 2009-10-19 23:23 14e6c3ab-a70a-461e-a35d-92795fabe5a8 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 -> ../../sda1
**lrwxrwxrwx 1 root root  10 2009-10-19 23:23 72773812-8d7c-4dc1-8fd0-a54966e49dd9 -> ../../sda2**
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 7b1c0cb0-03e3-481d-8248-67c88cbd936e -> ../../sdb3
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 86c77820-6029-4f2a-8a94-09d572e603c6 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 90272743-8704-454a-986c-e7cd45dfa8f0 -> ../../sda4
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 c51e0d86-07ad-4ac7-8f2c-bdf8f1b89e06 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2009-10-19 23:23 d6e3085e-47d6-4226-b317-514d2479873a -> ../../sdb1

I am confused.

Any insight would be appreciated.

/ running Mythbuntu 9.04

---

### Post by egalvan on 2009-10-20
fstab does not necessarily list the current UUID of partitions, it merely lists the UUID that the partitions had when fstab was created.


```
 ls /dev/disk/by-uuid -lah
```
will list the current UUID,

 as will
```
sudo blkid
```

I prefer the latter, as it give me more info that I want.

As it stands now, your swap is not being used.
And since sleep and hibernate use swap, these are also not working...

---

### Post by Elfy on 2009-10-20
You'll need to edit fstab and change the UUID - once done and saved

```
sudo swapon -a
```

Run ```
free -m
``` to check swap is being used.

Further check the UUID in here

```
cat /etc/initramfs-tools/conf.d/resume
```

If that UUID is wrong edit that as well and then run

```
sudo update-initramfs -u
```

---

### Post by cat2005 on 2009-10-20
egalvan, forestpixie,
 
So, if I understand correctly, you both are saying my "swap" is "turned off".  Am I correct?
 
I noticed a possibly related item using gparted in the live cd environment:  I see a "swap on" and "swap off" option.  I don't remember which was selected.  Could I "turn on" swap via live cd, or should I do it via the methods you described?
 
Thank you.

---

### Post by Elfy on 2009-10-20
You can do it from your system - but you do need to ensure that you have edited the UUIDs as shown before you do swapon

---

### Post by cat2005 on 2009-10-20
> **forestpixie said:**
> You can do it from your system - but you do need to ensure that you have edited the UUIDs as shown before you do swapon
 
So as a summary:
 
1) correct the swap UUID
2) turn on swap
 
Regarding "turn on", I don't fully understand "where" to "turn on" swap.  Must I do it via the commands you gave in terminal, or could I do it via the gparted gui while running a live cd?  
 
Thank you again.

---

### Post by Elfy on 2009-10-20
Yep 

get the correct UUID and then edit fstab and the resume files as above - then you can run swapon from a terminal.

Oncew you have run the command check with free -m see if your swap is recognised.

---

### Post by cat2005 on 2009-10-20
forestpixie,

I think I finished it.  Here is my terminal output.  FYI - Instead of "cat" that one file, I simply "gksudo" and edited.  

[B]mythprime@mythcpu:~$ sudo swapon -a
[sudo] password for mythprime: 

mythprime@mythcpu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1002        512        490          0         14        249
-/+ buffers/cache:        248        754
Swap:         2752          0       2752

mythprime@mythcpu:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 200 2009-10-20 18:13 .
drwxr-xr-x 6 root root 120 2009-10-20 18:13 ..
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 14e6c3ab-a70a-461e-a35d-92795fabe5a8 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 72773812-8d7c-4dc1-8fd0-a54966e49dd9 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 7b1c0cb0-03e3-481d-8248-67c88cbd936e -> ../../sdb3
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 86c77820-6029-4f2a-8a94-09d572e603c6 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 90272743-8704-454a-986c-e7cd45dfa8f0 -> ../../sda4
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 c51e0d86-07ad-4ac7-8f2c-bdf8f1b89e06 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 d6e3085e-47d6-4226-b317-514d2479873a -> ../../sdb1

mythprime@mythcpu:~$ sudo update-initramfs -u
[sudo] password for mythprime: 
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic

mythprime@mythcpu:~$ [/B]


1 - I edited the FSTAB on sda2. 
2 - ran "sudo swapon -a" 
3 - ran "free -m"  .....looking at the output, it seems to have worked
4 - got my new UUID for sda2 (ls /dev/disk/by-uuid -lah) (I also did this before step 1)
5 - edited initramfs via "gksudo" instead of "cat" (*I assume doing it this way was ok, correct?*)
6 - updated initramfs

_Questions_:
a)  Am I done?
b)  Could I repeat this process for my other harddrive if it has a similar problem?

Thank you so much!

---

### Post by Sir Jasper on 2009-10-20
Hi,

I would think it likely  ¨gnome-system monitor¨ is already installed and if you load it then click on the Resources heading you will see your swap usage.

If you click on the Processes heading you will probably find that the monitor itself uses quite a lot of resources - so may be best not left running.

My regards

---

### Post by Elfy on 2009-10-21
> **cat2005 said:**
> forestpixie,

I think I finished it.  Here is my terminal output.  FYI - Instead of "cat" that one file, I simply "gksudo" and edited.  

[B]mythprime@mythcpu:~$ sudo swapon -a
[sudo] password for mythprime: 

mythprime@mythcpu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1002        512        490          0         14        249
-/+ buffers/cache:        248        754
Swap:         2752          0       2752

mythprime@mythcpu:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 200 2009-10-20 18:13 .
drwxr-xr-x 6 root root 120 2009-10-20 18:13 ..
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 14e6c3ab-a70a-461e-a35d-92795fabe5a8 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 53cb4452-f63f-4f62-8fbf-aaeeabeb5d19 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 72773812-8d7c-4dc1-8fd0-a54966e49dd9 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 7b1c0cb0-03e3-481d-8248-67c88cbd936e -> ../../sdb3
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 86c77820-6029-4f2a-8a94-09d572e603c6 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 90272743-8704-454a-986c-e7cd45dfa8f0 -> ../../sda4
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 c51e0d86-07ad-4ac7-8f2c-bdf8f1b89e06 -> ../../sdb4
lrwxrwxrwx 1 root root  10 2009-10-20 18:13 d6e3085e-47d6-4226-b317-514d2479873a -> ../../sdb1

mythprime@mythcpu:~$ sudo update-initramfs -u
[sudo] password for mythprime: 
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic

mythprime@mythcpu:~$ [/B]


1 - I edited the FSTAB on sda2. 
2 - ran "sudo swapon -a" 
3 - ran "free -m"  .....looking at the output, it seems to have worked
4 - got my new UUID for sda2 (ls /dev/disk/by-uuid -lah) (I also did this before step 1)
5 - edited initramfs via "gksudo" instead of "cat" (*I assume doing it this way was ok, correct?*)
6 - updated initramfs

_Questions_:
a)  Am I done?
b)  Could I repeat this process for my other harddrive if it has a similar problem?

Thank you so much!

Yes you are done if all the swap UUIDs match now. 

Yes, I assume you edited with gedit - sort of assumed you knew that as you'd not asked how to :)

Yes the process is indeed repeatable wherever you need to do the same thing.

---

### Post by cat2005 on 2009-10-21
Hooray!  Thanks!

---

