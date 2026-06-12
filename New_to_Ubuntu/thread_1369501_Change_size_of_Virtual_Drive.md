---
title: "Change size of Virtual Drive"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by MikeSr39 on 2010-01-01
I have tried upgrading to latest version of Ubuntu and it tells me that the size of my drive is not big enough. It says change '/' size. I have Ubuntu installed originally using Wubi which created a virtual drive and put Ubu;ntu in there. My question is: How do I change the size of a "virtual drive" ??? Although I have had Ubuntu for over a year I am a novice at anything Linux. I also have a head injury so things have to be explained to me in "Little People talk"(step by step)
Thank you ahead of time,for your time.

Michael E. Califf,Sr.

---

### Post by Methuselah on 2010-01-01
I do not have a wubi install myself so I cannot give firsthand instructions.
However, I found a program called LVPM which allows you to move a Wubi installation to a dedicated partition OR resize the wubi virtual disk.
The latter is what you want to do.

See if you can install it with
> 
sudo apt-get install lvpm


The web page is below.
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

From the website:
> 
Resizing virtual disks using LVPM (not necessary if you're transferring the install to a dedicated partition)

Run LVPM, and once the menu appears, select either "resizehome" (to resize the /home virtual disk) or "resizeroot" (to resize the / virtual disk).

Input the new size, in MB, of the virtual disk.

Wait until the program finishes creating a new disks file and copying files from original home disk file; it will pop up a final instruction window instructing to backup the original home disk file and renaming the newly created disk file

Boot into windows and navigate to c:\wubi\disks, move the old virtual disk to a different folder as backup, and rename new.virtual.disk to home.virtual.disk (if you used resizehome) or system.virtual.disk (if you used resizeroot)

Reboot into ubuntu


---

