---
title: "Ubuntu says no space on hard drive."
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Shivendu on 2009-06-22
Hi All,  I am an absolute newbie to Ubuntu so please excuse if you find my questions stupid.  I recently received the Ubuntu CD and went ahead to install Ubuntu as dual boot option on my LAptop which was having Win XP Pro.  I wanted the Win XP as back up only so I made a 18 Gb partition( c:) on my hardrive and formatted the d: which is around 24 Gb.  During Installation I followed the option 1 Guided and installed Ubuntu 9.04. Now whenever I want to use update manager, I get a message saying there is not enough space on '/' . I am confused as to where Ubuntu has got loaded as I can still see that there is a drive with about 22 Gb free space ( and which I have to mount everytime I restart)  Trying to find the solution everywhere without any results. I am sure I followed all the steps correctly. Is it that Ubuntu has got loaded in the windows partition itself.  How can I make sure that Ubuntu uses all the 24 GB space available?  I am ready to erase and install Windows and Ubuntu again if need be.  Please help,  Shivendu.

---

### Post by ohzopants on 2009-06-22
Open the terminal and run:
```

cat /etc/fstab

```

Post the output of that command here and I may be able to help you.

---

### Post by Shivendu on 2009-06-22
> **ohzopants said:**
> Open the terminal and run:
```

cat /etc/fstab

```Post the output of that command here and I may be able to help you.

 Thanks a lot. will let you know asap

---

### Post by Shivendu on 2009-06-22
Hi This is what I got after tying cat /etc/fstab in terminal    # /etc/fstab: static file system information. # # Use 'vol_id --uuid' to print the universally unique indentifier for a  # device; this may be used with UUID= as a more robust way to name devices #that works even if disks are added and removed.See fsatb(5). # #            proc               /proc     proc     defaults     0        0 # / was on /dev/sda6 during installation UUID=423826ea-59b2-447d-989b-cf7f1792e75a/         ext3      relatime,error s=remount-ro 0    1 #swap was on  /dev/sda7 during installation UUID=d92cdde9-e16b-4db9-94b0-e2b461cc002e none     swap    sw    0     0 /dev/scd0      /media.cdrom0    udf,iso9660 user,noauto,exec,utf8 0      0  Thanks in advance

---

### Post by Elfy on 2009-06-22
Can you post the result of 

```
df -h
```

Also you can use [BBcode]("http://ubuntuforums.org/misc.php?do=bbcode") to format the output so it can be read - I use code and quote mostly - put [noparse]```
[/noparse] at the beginning of the pasted text and [noparse]
```[/noparse] at the end. Replace code with quote if you want to use that instead.

---

### Post by ugm6hr on 2009-06-22
> **Shivendu said:**
> During Installation I followed the option 1 Guided and installed Ubuntu 9.04.

I believe the default Guided installation option reduces the size of your primary partition (i.e. C: ) to install Ubuntu into.  So I suspect that your 18GB XP partition is now even smaller, with just enough room for Ubuntu.

As mentioned, **df -h** will tell you how much space you have.

Additional useful info from:
```
sudo fdisk -l
```

---

### Post by Shivendu on 2009-06-22
Thanks a lot for the useful tips 

Here are the results for df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G   13M 100% /
tmpfs                 241M     0  241M   0% /lib/init/rw
varrun                241M   92K  241M   1% /var/run
varlock               241M     0  241M   0% /var/lock
udev                  241M  148K  241M   1% /dev
tmpfs                 241M  168K  241M   1% /dev/shm
lrm                   241M  2.4M  239M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp 
```

And for sudo fdisk -l it gives me this info:-
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd700d700

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1619    13004586    7  HPFS/NTFS
/dev/sda2            1620        4864    26065462+   f  W95 Ext'd (LBA)
/dev/sda5            1620        4538    23446836    7  HPFS/NTFS
/dev/sda6            4539        4842     2441848+  83  Linux
/dev/sda7            4843        4864      176683+  82  Linux swap / Solaris 
```

I guess Ubuntu has been installed on the windows drive itself.

How can I install Ubuntu on the 24 gb free space...

Can I do it without re-formatting.

Thanks.

---

### Post by Shivendu on 2009-06-22
Please help as without this I cannot add/use any new features to Ubuntu.

---

### Post by Elfy on 2009-06-22
As you can see from df -h your drive is full

/dev/sda6             2.3G  2.2G   13M 100% /

You either need to resize drives to increase the space - use your livecd and there is a partition editor in the System Admin menu - make sure to turn swap off - right click the swpa partition, there is a swapoff command there.

If you decide to > How can I install Ubuntu on the 24 gb free space...when you install tell it to use free space at the partitioning section and not resize existing. Afterwards you will have the old install still unless you delete the partition.

---

### Post by Shivendu on 2009-06-22
Thanks, will let you know how things turn out.

---

### Post by Shivendu on 2009-06-22
Thanks a ton.  p.s. I am not able to find any button for closing the thread.

---

### Post by Elfy on 2009-06-22
> **Shivendu said:**
> Thanks a ton.  p.s. I am not able to find any button for closing the thread.

Glad your sorted - there is no button to close the thread ;)

---

