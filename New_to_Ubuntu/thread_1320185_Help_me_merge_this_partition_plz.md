---
title: "Help me merge this partition plz"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by gackt on 2009-11-09
Hi guys,

I want to merge a partition (ext 3) to existing partition (which contain windows xp for my dual boot) here is what gparted show me:

Partition File system Size  Flags
/dev/sda1 ext4        70.7  -----
/dev/sda2 Linux Swap  2.00  -----
/dev/sda3 NTFS        19.5  Boot
/dev/sda4 ext3        56.8  -----

I installed Ubuntu 9.10 on Sda1, sda2 is the Swap, sd3 is the windows ( dual boot)  and sda4 is unused partit. What i want is to have NTFS merge with ext3 without crashing the boot. how do i accomplish this? Thanks

---

### Post by jbrown96 on 2009-11-09
It shouldn't affect your boot at all. Let me explain how you grub works. Your BIOS boots, and selects a device to load: your hard drive. It reads the MBR (master boot record), which is a very small area at the beginning of your hard drive (not in a partition). The MBR is so small it can't really hold much. It loads the "first stage" of grub, which basically holds the location of the "second stage." This second stage is in your Ubuntu partition. Once stage two loads, then you get the menu where you can choose your OS. 
sda3 is actually never accessed during this, until you select XP from the menu. It won't do anything to merge sda3 and sda4. You wouldn't be able to do this painlessly if XP was a lower partition than Ubuntu because stage 1 of grub would point to the partition before Ubuntu. Since it's after, there shouldn't be any trouble. Note that choosing XP from the menu will cause errors, but that's pretty obvious. You may want to delete it from /boot/grub/menu.lst, but it's not essential.

---

### Post by gackt on 2009-11-09
Thanks jbrown96, 

Ok let me run this once again, so if i merge sda3 and sda4 i still can have my ubuntu run properly and windows too? Its windows partition that i'm worry about. I dont want to scrap it. Thanks

---

### Post by jbrown96 on 2009-11-09
Everything should fine because the partition numbers aren't changing for anything important: sda1, sda2, or sda3.

---

### Post by Mark Phelps on 2009-11-09
> **gackt said:**
> ... What i want is to have NTFS merge with ext3 without crashing the boot. how do i accomplish this? Thanks

You basically can not "merge" partitions, especially those formatted for very different file systems.

Basically, what you have to do is the following:
1) Boot into LiveCD
2) Run Partition Editor
3) Remove the NTFS partition
4) Confirm that the Ext3 partition is unmounted, if it's not, then unmount it
5) Expand the Ext3 partition to fill the unused space left behind by the NTFS partition.

You do realize, I hope, that anything left in the NTFS partition will be lost once you remove that partition, right?

---

### Post by jbrown96 on 2009-11-09
> **Mark Phelps said:**
> You basically can not "merge" partitions, especially those formatted for very different file systems.

Basically, what you have to do is the following:
1) Boot into LiveCD
2) Run Partition Editor
3) Remove the NTFS partition
4) Confirm that the Ext3 partition is unmounted, if it's not, then unmount it
5) Expand the Ext3 partition to fill the unused space left behind by the NTFS partition.

You do realize, I hope, that anything left in the NTFS partition will be lost once you remove that partition, right?

That's not at all what he wants to do. He wants to expand Windows to use the unused space in sda4.

It is strongly recommended that you use the "partition editor" in Ubuntu (either install it on your system or boot the liveCD) to delete sda4. Reboot into Windows. Right click on My Computer and select Manage. On the left choose the logical disk manager. You should be able to expand your Windows partition. 
NTFS is a Windows file system, and while Linux has good NTFS support, it's not a good idea to mess with a NTFS system drive with Linux. You never know what can happen; better to play it safe and use Windows to change Windows drives.

---

### Post by gackt on 2009-11-11
@ jbrown96
Exactly! Thank you so much. I'm giving it a try tonight.

@Mark Phelps
Thanks

---

