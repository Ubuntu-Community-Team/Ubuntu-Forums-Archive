---
title: "Mounting Other HDs? Why do i need permissions everytime?"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by LatinKid on 2010-03-29
So i Have 4 disks (3 working ATM); 1 is just a storage disk, another is Windows XP Pro SP3, and the last one is Xubuntu x64 9.10. I am on Xubuntu and everytime i want to access one of the other disks, i have to (i think its kinda smart, but it wouldn't be if i didn't have this problem) open a zipped file, click extract, and on the side of the new window that pops out, i choose (e.g.) Jesse's Drive, and i have to enter my password. Same thing for Windows, except if I opened Jesse's Drive before Windows, then i would just open windows in the extract window, wait a few seconds, then voila, i can view these HDs under /media/*. I would like to know a way for me to not have to do this every time I log in.

---

### Post by sisco311 on 2010-03-29
Hi and welcome to the forums!

Mount the partition(s) at boot time:
[http://psychocats.net/ubuntu/mountwindows#ntfsconfig](http://psychocats.net/ubuntu/mountwindows#ntfsconfig)

---

### Post by itisbasi on 2010-03-29
Automount your drives using pysdm and configure them to mount at login.
[http://dizzietech.wordpress.com/2009/10/19/pysdm-a-user-friendly-application-to-automount-your-disk-in-ubuntu/](http://dizzietech.wordpress.com/2009/10/19/pysdm-a-user-friendly-application-to-automount-your-disk-in-ubuntu/)

---

### Post by LatinKid on 2010-03-29
Thanks a bunch, sisco311__

---

