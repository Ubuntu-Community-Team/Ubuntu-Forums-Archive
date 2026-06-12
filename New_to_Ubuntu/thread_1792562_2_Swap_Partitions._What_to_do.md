---
title: "2 Swap Partitions. What to do?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Moonraise on 2011-06-28
Hello Everyone,

Using Gparted I discovered that I have 2 Swap Partitions. Seeing how there is no point in having 2 when I only have 1 Linux-based OS, I tried to simply delete the unused one using Gparted. However I received this error[IMG]http://i.imgur.com/ZuVtE.jpg[/IMG]


Is there an easy way to remove this, or should I just not bother? It's not like I need the extra space as long as it's stable and fast. I doubt that an additional partition can slow down my Computer.

I'm relatively new to Linux, so I installed 11.04 64-bit on my PC as dual-boot with Win7. (Hence the big NTFS Partition)

I hope you guys can help me decide here.
Thanks in advance

---

### Post by Paqman on 2011-06-28
The problem is that the swap partition is inside your extended partition, which is mounted whenever your machine is running.

Just delete the other one instead.

---

### Post by eriktheblu on 2011-06-28
Right click and select "Swapoff" before attempting to delete.

---

### Post by Paqman on 2011-06-28
Actually, sorry, I read that wrong. Both your swap partitions are inside your extended partition. That means you'll be unable to delete them from your normal system. You'll have to boot up into a LiveCD or USB, run Gparted, "swapoff" and delete one of them.

---

### Post by Moonraise on 2011-06-28
> **Paqman said:**
>  "swapoff" and delete one of them.
Dont I need to activate any of them or will they automaticly set themself up once booted?

---

### Post by Paqman on 2011-06-28
> **Moonraise said:**
> Dont I need to activate any of them or will they automaticly set themself up once booted?

You don't _need_ to have a swap partition available unless you start running out of memory. But yes, they get automatically mounted at boot. If you want to be tidy you can comment out the entry in the file that makes them mount automatically.
Hit Alt-F2 and type:
```
gksudo gedit /etc/fstab
```
...and add a # to the start of the line that corresponds to the swap partition you deleted. Save and exit.

---

### Post by oldfred on 2011-06-28
If you have 4GB or more of RAM and do not hibernate you can get by without swap unless you load some very large programs like editing video or like to load many program at once.

You do have to delete from liveCD and liveCD will normally mount swap(s) to speed up liveCD. click on swap and right click swap off to unmount them. Then you can delete one or the other.

It will not automount a new swap if you delete the current one you are using. The entry in fstab is not automatically updated. You can manually update it with the correct UUID if you want.

To see UUID

sudo blkid

---

