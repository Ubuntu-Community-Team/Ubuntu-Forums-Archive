---
title: "Partition Check"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by flotoonie on 2011-06-06
Gday all

I am about to try and dual boot some Linux distros with Win7 on my Asus G1S laptop.  I was hoping you could give me some feedback on the partitions I have set up.  If I have done something wrong or if I can do it better please let me know.

Here is the setup EASEUS partitioner is showing me in Win7;

*: System Reserved NTFS 100mb (used 28mb)Status:System Primary  (No idea what this is for)
C: NTFS 35gb Status:Boot Primary
Bunch of logical partitions (See Below)
*: Swap 2gb Primary

The Logical drives are for the Distros with 10gb for each, a partition for me to dump stuff I can access from Win7, and also two logical drives for /boot and /home

I have dual booted before but only with Win Xp and Ubuntu a couple of years ago.

I have seen some tutorial regarding dualbooting but none as of yet that show multiple distro dual boots.

Cheers

---

### Post by oldfred on 2011-06-07
Your 100MB system partition is windows boot/recovery partition. Do not change or use it for anything else.

You cannot share /boot across distributions. For standard desktops you do not need a separate /boot. I think it is Fedora that has a /boot but that is because the install is in a LVM partition. You also can only really share a /home if you use different user name as UID & GID may be different across distributions. Also each distribution may use different versions of the same programs where settings may conflict.

If all installs are Debian based so UIDs are all 1000, then you can use a /data partition easily and share data and keep /home with just user settings inside the root partition. Also if using windows you may just want most of you data in a NTFS shared data so you can shared with all distributions. I still use my NTFS shared for my Firefox & Thunderbird profiles even though I do not boot XP hardly at all anymore.

---

### Post by flotoonie on 2011-06-07
Thanks for your reply oldfred :)

So the following partitions should work for me?

(P) - Primary
(L) - Logical

System Reserved (P)
C:/(P)
Ubuntu (L)
Distro2(L)
Distro3(L)
Distro4(L)
Common (NTFS)(L)
Swap(P)

Thanks again :)

---

### Post by oldfred on 2011-06-07
That should work. 

When I got my newer larger hard drive, I did not full partition it. I added a couple of larger data partitions, one NTFS & one ext3. But now I find I am just adding 20 or 25GB root partitions. I have my old versions of Ubuntu still bootable and a few others that I have tried.

---

### Post by flotoonie on 2011-06-11
Thanks mate :)

---

