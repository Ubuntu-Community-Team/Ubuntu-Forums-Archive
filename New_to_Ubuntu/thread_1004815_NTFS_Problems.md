---
title: "NTFS Problems"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-12-07
I have a 500 gig external HD and everything worked fine until a couple weeks ago.  Now it is not mounting it as readable/writable just readable.  
I have downloaded NTFS configuration progs but still nothing.  Any help would be appreciated.

---

### Post by MarblePanther on 2008-12-07
sudo chmod -R a=rw "the disk path"

---

### Post by lisati on 2008-12-07
Please forgive me if you've already checked this, you might need to access the HD from Windows and then use the "safely remove hardware" option before Ubuntu will touch it.

---

### Post by gettinoriginal on 2008-12-07
You can see if this will help.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by LowSky on 2008-12-07
> **lisati said:**
> Please forgive me if you've already checked this, you might need to access the HD from Windows and then use the "safely remove hardware" option before Ubuntu will touch it.

Exactly.. this happens if a windows computer is accessing the drive and then not disconnect properly, do what lisati explained usually fixes the problem

---

### Post by kansasnoob on 2008-12-07
Since this is Xubuntu if all else fails try:

```
sudo apt-get install --reinstall thunar
```

While the drive is plugged in.

---

### Post by KuroYoma on 2008-12-08
Can't be windows only use that for gaming.  I will try the chmod command. and then the reinstall command.  If i can find enough space to store all my files on i will just switch it to ext3fs.  I will let you know how it went later thanx

---

### Post by egalvan on 2008-12-08
> **KuroYoma said:**
> **Can't be windows only use that for gaming.**  I will try the chmod command. and then the reinstall command.  If i can find enough space to store all my files on i will just switch it to ext3fs.  I will let you know how it went later thanx

Doesn't matter what you use XP for; if the drive is connected when XP boots, then it's 'touched', and needs to be either safely removed via the proper function, or XP needs to be shut down.

Otherwise, the file system is 'dirty' and Linux will (rightly) refuse to open it as Writable.

Other situations can also cause this behavior. This is just the most common one.

And yeah, switching to ext3 is a great option.,
Then you can use **Ext2 Installable File System For Windows**

[http://www.fs-driver.org/](http://www.fs-driver.org/)

and yes, it works on ext3, I've been using it since March with no problems (on several different machines).

---

