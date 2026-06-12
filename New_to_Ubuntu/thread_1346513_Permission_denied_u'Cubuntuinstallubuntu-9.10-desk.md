---
title: "Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by fchartier on 2009-12-05
Hi all, 

I have been trying to install ubuntu using wubi. At the end of the install it crashes, and here is the log message. It a case of permission error. perhaps the path where it installs the file is too long(?)
here is the end of the log file 
cheers & Thanks a lot

 in task download
12-05 12:10 DEBUG  TaskList: ### Finished download
12-05 12:10 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
12-05 12:10 DEBUG  TaskList: # Cancelling tasklist
12-05 12:10 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
12-05 12:10 DEBUG  TaskList: # Finished tasklist

---

### Post by Chesnut on 2009-12-05
A random guess:

Run it as administrator?

---

### Post by fchartier on 2009-12-05
sorry for my ignorance, but how come i am not already adminstrator ? its my personal laptop... if not how do i run it as administrator
Thanks

---

### Post by fchartier on 2009-12-05
I have just checked in control panel, I am administrator...

---

### Post by Terl on 2009-12-05
> **fchartier said:**
> sorry for my ignorance, but how come i am not already adminstrator ? its my personal laptop... if not how do i run it as administrator
Thanks

Are you using Vista perhaps?  If so right click the icon before you run it and select "run as administrator".

I know it is your own laptop but Vista (and maybe windows 7) changed security.

---

### Post by fchartier on 2009-12-05
Thanks Chestnut and Therl,

I will try that. Although I am still in windows Xp 2002..
I will keep u updated
cheers

---

### Post by Terl on 2009-12-05
> **fchartier said:**
> Thanks Chestnut and Therl,

I will try that. Although I am still in windows Xp 2002..
I will keep u updated
cheers

Okay, you are using XP, then my idea won't work.  There is definitely a permissions issue in the log, but I've never used wubi so I am unfamiliar with the way it works.

I found some assistance [here]("https://bugs.edge.launchpad.net/wubi/+bug/207137") and more [over here]("https://bugs.launchpad.net/wubi/+bug/383840").  Read through the threads, they have some ideas to help

---

### Post by fchartier on 2009-12-05
Apparently someone in the launchpad met with the same pb according to your last comments. I will try to follow these and we shall see.
cheers
and thanks for ur help

---

### Post by 3rdalbum on 2009-12-05
Try downloading the Ubuntu disc image yourself, burning it to disc and running the Wubi installer from the disc. It will then be accessing the CD, not Windows' C: drive.

Better yet, burn the disc, boot up from it and install Ubuntu as a dual-boot from there; it will avoid all the limitations of the Wubi install. Just make sure you back up all your data first, because it involves (non-destructively) repartitioning your hard drive. I say "non-destructively", but in reality any partitioning operation can go wrong.

---

### Post by m4d_hat on 2009-12-05
You can also manually modify user permissions by right clicking the .iso and selecting properties. Click the "security tab" and you can add a group called "everyone" and select all permissions minus full control and that should allow the application to access the file. 

However, I tend to agree with 3rdalbum in that burning the cd would be more appropriate in this situation.

---

### Post by alzie on 2009-12-05
I would suggest downloading Ubuntu 9.10 from Ubuntu.  Place the newly downloaded 9.10 into a folder along with the wubi icon.

This way wubi will use the downloaded ISO rather than trying to download one from the net itself. This is how I installed wubi.

If this doesn't work,  you can go into "add and remove software" to find wubi and remove it.  The go into "my computer, look for a file called Ubuntu which should have wubi and an old Ubuntu ISO in it.  Delete this whole file and then try again.  This shouldn't be necessary as wubi should manage this automatically but might be needed.

I hope this helps.

---

### Post by DustWolf on 2010-02-13
Experiencing the same problem.

Filed a bug report at:
[https://bugs.launchpad.net/wubi/+bug/521489]("https://bugs.launchpad.net/wubi/+bug/521489")

---

### Post by RiffRaff06078 on 2010-03-04
> **alzie said:**
> I would suggest downloading Ubuntu 9.10 from Ubuntu.  Place the newly downloaded 9.10 into a folder along with the wubi icon.

This solution resolved the permissions problem for me.  Thanks!  :KS

---

