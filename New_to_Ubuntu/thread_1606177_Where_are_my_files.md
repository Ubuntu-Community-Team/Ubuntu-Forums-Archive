---
title: "Where are my files"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Eastwood1 on 2010-10-26
Hi, you fundi. I have installed Ubuntu on my (Internal) harddrive. I also have an external harddrive. Now, ubuntu accesses the external harddrive (300 gig) to get my files Music,photos/flies etc but cannot find any files on my internal  harddrive (80 gig) I have a choice on starting up: 1. XP 2. Ubuntu. I know its something I dont or do that causes this! Please help one of you experts. Keep in mind that I am electronically retarded (disadvantage)= born before '65:guitar:

---

### Post by LiamWilson on 2010-10-26
Fist off, let's try to clear something up, you installed ubuntu alongside windows, and you want to access your windows XP files, yeah?

Can you boot into windows from the choices at starting up?

---

### Post by ikt on 2010-10-26
> **Eastwood1 said:**
> but cannot find any files on my internal  harddrive (80 gig)

When you click on places then computer, do you see the name of your 80GB hard drive listed?

There is also the Disk utility found by going:

System > Administration > Disk Utility

Does it list your 80GB internal hard drive?

---

### Post by coffeecat on 2010-10-26
If you installed Ubuntu side-by-side with Windows in the 80GB drive with Ubuntu in its own partition, then you will be able to access the Windows C: partition by going to the Places menu and finding the Windows partition listed either within the Places menu itself or under "Removable Media"

If you installed Ubuntu as a Wubi install ("inside" Windows) then you can access the Windows C: drive by going to the Places menu, choosing "Computer", double-clicking on File System in the window that opens, and then double-clicking on the 'host' folder.

---

### Post by Eastwood1 on 2010-10-26
Thanks sofar , (UBUNTU partitioned installation) but:
On the places menu you get the vertical menu that starts with
Homefolder
Desktop
Documents
.
.
.Computer
Fresh (my ext HD)
Floppy
Click on computer and a horisontal Menu appears
CD-RW   Floppy  Fresh  Filesystem
Click on Filesystem , taking that it is the Int HD and 25 icons appear bin boot cdrom dev etc .......vmlux.old
Am I now completely lost?

---

### Post by Verbeck on 2010-10-26
how did you install ubuntu? from within windows or from the live cd?


EDIT: found something from the ubuntu wiki: might help if you did a wubi install

> The Windows partition where you installed Wubi is available as /host  within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media 

---

### Post by Perseverance on 2010-10-26
In the computer section you must have Host filesystem

---

