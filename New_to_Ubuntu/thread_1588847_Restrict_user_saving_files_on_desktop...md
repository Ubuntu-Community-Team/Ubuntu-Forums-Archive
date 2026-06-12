---
title: "Restrict user saving files on desktop.."
date: 2010-10-05
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-05
Is it possible to restrict  user saving files on desktop..?

---

### Post by krishnandu.sarkar on 2010-10-05
As far I know user can save files on their desktop and you can't restrict that.

---

### Post by viralmeme on 2010-10-05
> **getyourkarthick said:**
> Is it possible to restrict  user saving files on desktop..?

You could make /home/user/Desktop/ readonly ..

$sudo chmod u-w /home/user/Desktop/

---

### Post by karthick87 on 2010-10-05
> **viralmeme said:**
> You could make /home/user/Desktop/ readonly ..

$sudo chmod u-w /home/user/Desktop/

Fine it worked..But can you explain me the above command what is u-w

---

### Post by HermanAB on 2010-10-05
Howdy,

The desktop is a directory like any other.  Therefore you can make it read-only if you want.

---

### Post by viralmeme on 2010-10-06
> **getyourkarthick said:**
> Fine it worked..But can you explain me the above command what is u-w

Under Linux access to files-and-directories are granted to three groups, owner, group and world. Access are further granted as Read, Write or Execute. So, `sudo chmod u-w /home/user/Desktop/' means remove the write attribute for the owner. Everything is a file in Linux so the same principle applies to all the hardware.

[Linux Files and File Permission]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")

---

### Post by karthick87 on 2010-10-06
> **viralmeme said:**
> Everything is a file in Linux so the same principle applies to all the hardware.


How do you say that everything is a file in linux.What about in windows..?

---

### Post by viralmeme on 2010-10-06
> **getyourkarthick said:**
> How do you say that everything is a file in linux.What about in windows..?
[On A Linux System Everything Is A File ]("http://www.linuxpronews.com/linuxpronews-55-20080610OnaLinuxSystemEverythingisaFile.html")

---

### Post by da burger on 2010-10-06
> **getyourkarthick said:**
> How do you say that everything is a file in linux.What about in windows..?
 
Just to answer from a windows point of view (which I think is what you wanted) in windows there are (to my understanding) some pieces of data on the partition that windows doesn't register within the file system. They are referenced by their location on the drive.
Hope this helps
Angus

---

