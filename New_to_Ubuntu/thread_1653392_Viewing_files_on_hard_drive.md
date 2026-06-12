---
title: "Viewing files on hard drive"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by pudi211 on 2010-12-26
Is it possible to see my files on my hard drive?  It appears I can't access it from ubuntu, but I can still access them from windows.  I am running both systems until I get used to ubuntu.

---

### Post by daredevil82 on 2010-12-26
See what files?  on what OS?

---

### Post by pudi211 on 2010-12-26
my files that are on the windows hard drive, pictures, music, documents, etc

---

### Post by -kg- on 2010-12-26
Yes.  Assuming you are running Ubuntu (and not Kubuntu, Xubuntu, or another variation), go to the top tool bar, click on "Places" (Top left) and click on "computer" from the list.  Once there, you should see all your partitions on all hard drives.

You will need to double-click on your Windows partition(s), which will likely not be auto-mounted.  This will mount it/them.  Then it's just a matter of browsing them as normal.

---

### Post by pudi211 on 2010-12-26
I'm still not seeing them...it is like ubuntu is not reaching out to the hard drive...could it be a software issue?

---

### Post by amjjawad on 2010-12-27
Is this a normal installation or Wubi?

---

### Post by karthick87 on 2010-12-27
You have to mount your NTFS drives for that..First of all is that clear dual boot installation or you installed ubuntu inside windows using wubi?

---

### Post by pudi211 on 2010-12-28
I installed ubuntu inside of windows.  How do I mount the hard drives?  That is the error I get that the drive isn't mounted.

---

### Post by karthick87 on 2010-12-28
Post the output of,
```
sudo fdisk -l
```

---

### Post by WubiKeener on 2010-12-29
> **pudi211 said:**
> Is it possible to see my files on my hard drive?  It appears I can't access it from ubuntu, but I can still access them from windows.  I am running both systems until I get used to ubuntu.

I'm a newbie too ... if your install is a WUBI look in: 
>> Places >>Computer ... Open the "File System" folder and then the "Host" folder, you're looking at C:\

Hope that helps ..
Dave

---

### Post by Mark Phelps on 2010-12-29
Since you're using Wubi, it would do you good to read the following:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?")

The answer to your question is in 8.13.

---

