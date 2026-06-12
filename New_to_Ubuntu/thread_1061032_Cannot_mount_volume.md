---
title: "Cannot mount volume"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-02-05
Hy guys!
I have a problem with my partitions.I can't mount them anymore :(
I dual boot Ubuntu 8.04 and Windows XP and I have 3 partitions: one for windows (NTFS) one for data (NTFS) and one for Linux (ext 2).Today Windows crashed (what a surprise, no? :D) when my brother tried to start it and now I get the following error when I try to access NTFS partitions.
I tried what adding the files to /etc/fstab and it still doesn't work.
What can I do?

---

### Post by apjone on 2009-02-05
Nice desktop !!

open aterminal and run 

```

sudo mount /dev/sda1 /mnt -o force
sudo umount /mnt
exit

```

And then try to mount it

---

### Post by Eisenwinter on 2009-02-05
Windows needs to be shut down cleanly.

If you can access it, boot into Windows, and shut it down properly.

---

### Post by apjone on 2009-02-05
The ```
sudo mount /dev/sda1 /mnt -o force
``` clears the lock without having to boot windows

---

### Post by Troll_the_Great on 2009-02-05
> **apjone said:**
> 
open aterminal and run 

```

sudo mount /dev/sda1 /mnt -o force
sudo umount /mnt
exit

```

And then try to mount it

Thanks, that did it!

What exactly did those commands do?

PS:glad you like my desktop :)

---

### Post by apjone on 2009-02-05
No problem, stumped me when I first started lol. Great command if you are using live cd to grab files off bust Windows Machine before a reinstall.

---

### Post by Troll_the_Great on 2009-02-05
> **Eisenwinter said:**
> Windows needs to be shut down cleanly.

If you can access it, boot into Windows, and shut it down properly.

Windows is completely f...ed so I can't boot in it.I have to reinstall it and then repair the MBR because it will f..k that too!

---

### Post by Troll_the_Great on 2009-02-05
Apjone, what did those commands do?

---

### Post by apjone on 2009-02-06
```
sudo mount /dev/sda1 /mnt -o force
```
Forces the drive to mount to /mnt even if it was not shutdown correctly. NTFS creates a lock file which basically shouts at systems "I AM ALREADY MOUNTED" when its in use. Part of NTFS unmount / Windows shutdown removes this.......... unless it crashes or power is pulled.

```
sudo umount /mnt 
```
umounts the volume allowing you to remount it where it should mount.

---

