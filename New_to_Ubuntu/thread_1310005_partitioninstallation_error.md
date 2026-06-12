---
title: "partition/installation error"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by ave2 on 2009-11-01
I am trying to install 3 o/s windows xp, ubuntu 9.10 and ultimate edition, but it didn't work, so I was wondering what I did wrong.

I created 5 partitions:
1) primary NTFS for windows 
2) primary Ext4 for /
3) primary 10GB not formatted
4) logical Ext4 for /home
5) primary 2GB swap

windows was already installed

then installed 9.10
everything was fine till here

then ran ultimate edition install cd

formatted partition 3 as Ext3 for / based on 8.10, so doesnt use ext4

it then told me it was formatting partition 3 and partition 5(swap)
installed it
restarted, and 9.10 is no longer in boot up menu

I dont know where I went wrong

---

### Post by The Cog on 2009-11-01
I think the grub on your MBR is the grub installed by 8.04. And it is using the menu.lst created by 8.o4 which presumably doesn't understand ext4.
You may be able to use the rescue mode of a 9.10 "alternate" installer CD to boot the 9.10 partiton and then run grub-install /dev/sda from there.

As a last resort, reinstalling 9.10 will sort things out.

---

### Post by Miljet on 2009-11-01
I think that you are mistaken as to how your partitions are laid out. You can only have 4 primary partitions, one of which can be an extended partition which can contain numerous logical partitions. You cannot have 4 primary partitions AND a logical partition.

---

### Post by The Cog on 2009-11-02
> **Miljet said:**
> I think that you are mistaken as to how your partitions are laid out. You can only have 4 primary partitions, one of which can be an extended partition which can contain numerous logical partitions. You cannot have 4 primary partitions AND a logical partition.

That'a a good point. Now I'm feeling silly for not spotting that myself. These two commands should help understand what's really there:
```
sudo fdisk -l
sudo blkid -s TYPE
```

---

### Post by phelun on 2009-11-02
I think the 9.10 should be your last os to be installed..
So all other os on your pc ,boots from the genaral linux menu!!

I suggest you install your xp,run bdc vista booting app. ,then next the ultimate version and lastly the 9.10...
hope this helps you ,good luck!!:)

---

### Post by foottuns on 2009-11-02
> **ave2 said:**
> I am trying to install 3 o/s windows xp, ubuntu 9.10 and ultimate edition, but it didn't work, so I was wondering what I did wrong.

I created 5 partitions:
1) primary NTFS for windows 
2) primary Ext4 for /
3) primary 10GB not formatted
4) logical Ext4 for /home
5) primary 2GB swap

windows was already installed

then installed 9.10
everything was fine till here

then ran ultimate edition install cd

formatted partition 3 as Ext3 for / based on 8.10, so doesnt use ext4

it then told me it was formatting partition 3 and partition 5(swap)
installed it
restarted, and 9.10 is no longer in boot up menu

I dont know where I went wrong


why don't you use virtual system, like vwmare, virtualbox or xen, if you want to use a few os systems try to do a virtualization

---

### Post by ave2 on 2009-11-02
> **phelun said:**
> I think the 9.10 should be your last os to be installed..
So all other os on your pc ,boots from the genaral linux menu!!

I suggest you install your xp,run bdc vista booting app. ,then next the ultimate version and lastly the 9.10...
hope this helps you ,good luck!!:)

this worked, thanks everyone

btw my partitions were messed up, I found that ultimate edition wouldnt allow me to install anything, so I created 2 partitions, one for / and one for /home and that worked, then installing 9.10 last it finally can now boot into all three o/s

---

### Post by Xomm on 2009-11-02
> **foottuns said:**
> why don't you use virtual system, like vwmare, virtualbox or xen, if you want to use a few os systems try to do a virtualization

I know this thread is solved, but I have to point out:

VMing takes up a lot of resources, and if you don't have much to give, it's not that efficient.

---

### Post by LewRockwell on 2009-11-02
> **Xomm said:**
> I know this thread is solved, but I have to point out:

**VMing takes up a lot of resources, and if you don't have much to give, it's not that efficient.**

ditto

.

---

