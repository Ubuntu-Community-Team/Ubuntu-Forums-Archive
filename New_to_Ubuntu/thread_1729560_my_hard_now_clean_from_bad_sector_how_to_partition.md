---
title: "my hard now clean from bad sector how to partition it"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by magedsoft on 2011-04-15
hay my friends : 
 
my hard now is clean from bad sectors i want to partition it for just this time ,because i formatted many time , and i hope to partition it and don't formatted again .
 
i want to install ubuntu 10.10 i know how to do that i install it many time and i know how to do that but i need some hints or notes from you my friends here to make things clear .......
 
* there are ext2 ,ext3 .ext4 which better to filesystem
 
*which better to use partition program to partition my hard disk to ntfs drive "i know the root must be ext" i talking about the rest of hdd ,or i use ubuntu cd and mount hdd as example /media/movies or media/songs like that which better
 
*can i make 20 gb for /var to download apps as i want
 
* i usually copy data from my hdd to my friends hdd , how to increase the copy speed
 
i make thread here and my friends told my ntfs to ntfs will increase the speed
can i do it and use ntfs or ext,but i try it ntfs to ntfs and the speed was 20 mb/sec

my  computer specs
ram. 4 gb[/COLOR]
mb . gigabyte g41 combo
cpu . 2.7\2m duel core
hdd .1 tb
 
 
thank you

---

### Post by lisati on 2011-04-15
Please use the default font size and colour.

---

### Post by Paqman on 2011-04-15
> **magedsoft said:**
> 
* there are ext2 ,ext3 .ext4 which better to filesystem


They're all the same filesystem, just different versions of it. Ext4 is the newest and best.
 
> *which better to use partition program to partition my hard disk to ntfs drive "i know the root must be ext" i talking about the rest of hdd ,or i use ubuntu cd and mount hdd as example /media/movies or media/songs like that which better

If you're dual-booting with Windows then NTFS is a good choice for a shared data partition. If Linux is your only OS then I would use a Linux filesystem such as Ext4.
 
> *can i make 20 gb for /var to download apps as i want

You could, but I don't think there would be much point.
 
> * i usually copy data from my hdd to my friends hdd , how to increase the copy speed

Use a fast bus. The fastest way would be to open the case and plug both drives into SATA headers on the same machine and copy/sync your data over. USB is quite slow for large amounts of data.

---

### Post by Grenage on 2011-04-15
> **Paqman said:**
> Use a fast bus. The fastest way would be to open the case and plug both drives into SATA headers on the same machine and copy/sync your data over. USB is quite slow for large amounts of data.

If there's no ESATA port, a card is definitely worth the few quid.   I *believe* that NTFS on linux is also slower than than in Windows, but I've not yet had the chance to test it.

USB2 is horrible for large data transfers.

---

