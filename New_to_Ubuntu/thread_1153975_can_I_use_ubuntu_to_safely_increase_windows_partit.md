---
title: "can I use ubuntu to safely increase windows partition?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by aBitLater on 2009-05-09
Hi, 
I have windows on one disk, and ubuntu on a second disk.  The first disk with windows xp has several partitions because I was trying opensuse.  I no longer want opensuse, and I want to increase the size of the windows partition to fill the whole disk.  

Can I use gparted (gnome partition editor) from ubuntu on the 2nd disk to do this safely?  Will windows xp freak out when I boot into it after repartitioning?

Thanks for the help.

---

### Post by aikiwolfie on 2009-05-09
It should work fine. Just open gparted and delete the SuSE partition and expand the XP partition. It's always a good idea to back up your data though. Resizing partitions can take a while for the system to process everything. So if it's taking a very long time. Don't panic. Let it do it's thing.

---

### Post by Dougie187 on 2009-05-09
yeah it should work. If it doesn't work you can always use it from the live cd. But since you have two disks it should work. I believe you will have to unmount your windows drive though.

---

### Post by BoogeyOfTheMan on 2009-05-09
I recently did this with my Vista partition. It should work fine. Have your XP disk handy though in case you need to repair the install. After the resize, Vista wouldnt boot, but I just put in the disk and told it to repair, and then windows booted and seemed to work fine. That was about a month or so ago and I havent booted into it since or used it for anything after I got it working. 

So in summary, yes, it will work, make sure you have backups in case it doesnt, have an XP install disk handy in case you need to repair.

---

