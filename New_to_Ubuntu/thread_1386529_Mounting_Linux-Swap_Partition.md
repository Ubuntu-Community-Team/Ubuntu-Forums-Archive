---
title: "Mounting Linux-Swap Partition"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by rbscairns on 2010-01-20
Ubuntu 9.10

My eee B202 has 2GB RAM and 160GB HDD. The HDD is partitioned as shown in the following GParted screenshot.

It would appear that my /dev/sda5 linux-swap partition is not mounted. How do I mount this partition?

---

### Post by mikewhatever on 2010-01-20
Don't think you need to explicitly mount swap, at least I never have.

---

### Post by louieb on 2010-01-20
temporary
```
sudo swapon /dev/sda5
```automatic

get the uuid  ```
sudo blkid -c /dev/null
```make sure the uuid of sda5 matches the uuid of swap in **/etc/fstab**

---

### Post by drs305 on 2010-01-20
Your swap should have an entry in /etc/fstab.

Find the swap UUID:
```

sudo blkid -c /dev/null | grep swap

```

Open fstab for editing as root:
```
gksu gedit /etc/fstab
```

Look for one of these two entries.

Preferably, it's listed with a UUID - substitute your swap UUID for the one in the entry:
```

UUID=*b0e26f5f-a944-4fe7-8a5f-b3c2dc1bf5c7* none   swap  0   0

```
 or
> /dev/sda5   none  swap    sw   0       0

If it isn't listed, add the line and save the file, then "sudo mount -a" or "sudo swapon -a"

---

### Post by rbscairns on 2010-01-20
> **drs305 said:**
> Your swap should have an entry in /etc/fstab.

Find the swap UUID:
```

sudo blkid -c /dev/null | grep swap

```

Open fstab for editing as root:
```
gksu gedit /etc/fstab
```

Look for one of these two entries.

Preferably, it's listed with a UUID - substitute your swap UUID for the one in the entry:
```

UUID=*b0e26f5f-a944-4fe7-8a5f-b3c2dc1bf5c7* none   swap  0   0

```
 or


If it isn't listed, add the line and save the file, then "sudo mount -a" or "sudo swapon -a"
I was going well, until I find that I do not have the fstab file.```
gksu gedit /etc/fstab
```returns an empty Gedit window. A file search for fstab also produces no result.

What do I do now?

---

### Post by louieb on 2010-01-20
Try again. Its there - essential system file - 

Make sure you entered the command just as drs305 gave.

I've fat fingered etc - typing it ect lots of times.

---

### Post by majickmann on 2010-01-20
Open a terminal and run the command "free"...

This will display swap on the last line.  For example:

homer@simpson:~$ free
             total       used       free     shared    buffers     cached
Mem:       2058448     958844    1099604          0      24992     536608
-/+ buffers/cache:     397244    1661204
Swap:      1646620          0    1646620

As you can see my box has a little over 1.6G of swap available, but not using any.

Hope this helps...
:-)
--majickmann

---

### Post by rbscairns on 2010-01-20
You are right louieb. It is there. I have found it in etc - File Browser. The problem is that it is an empty file (size = 0 bytes) so there are no entries to find, check or edit in Gedit /etc/fstab.

Where to now?

---

### Post by warfacegod on 2010-01-20
I apologize for jumping in but I don't see what the problem is here. If you have Gparted (obviously you do) then right click your swap partition while in Gparted. The menu that comes up will say either *swap on* or *swap off*. If it says *swap off* (and it should) selecting it will turn your swap off and vice versa.

Again, my apologies if I've missed something here.

---

### Post by rbscairns on 2010-01-20
Thank you warfacegod. I feel like a chump for not seeing that earlier.

Problem solved!

---

### Post by drs305 on 2010-01-21
The problem may not be solved. The question remains why swap was not mounted in the first place. 

Swap should have been mounted by the setting in fstab. The next time you boot, check to see if swap was correctly mounted. You can check with gparted or you can run the "free -m" or "mount" command to determine if swap was correctly mounted during boot.

---

### Post by louieb on 2010-01-21
:confused: learned something new today - never seen a working Linux install with an empty /etc/fstab. Guess it makes sense - GRUB tells the kernel where the root file-system is -  and not using another partition for some other part of the file-system.

Anyway far as I know you will need an fstab entry to get swap to mount automatically at boot - unless you want to run the swapon command after every reboot. :D

---

### Post by rbscairns on 2010-01-21
The missing fstab file is another problem that I amworking on in another thread. I believe in one problewm per thread.

---

