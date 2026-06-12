---
title: "create an ISO image"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by d475719 on 2010-11-19
Hi, I'm fairly new to linux. I am using Ubuntu right now and my hard drive seems to be failing. I have a lot of things loaded on it so far such as applications, etc. with my personal settings. Is there any way I can create an ISO image with all of my things and put it on a CD so I can just get everything back into the new hard drive with all of my desktop settings, etc. saved?

Thank you for any help!

---

### Post by mbergamo on 2010-11-19
1. Open up Brasero (Applications > Sound and Video > Brasero Disk Burner).
2. Click on Data Project click on the** button (or go to Project > New Project > New Data Project)
3. Change the name of the disk at the bottom to whatever you want. 
4. Click the green plus sign on the top left to add the files you want.
5. When you're finished adding the files, make sure there is an empty CD/DVD in the drive and click Burn.

Hope this helps. 
**

---

### Post by ssulaco on 2010-11-19
> **d475719 said:**
> Is there any way I can create an ISO image with all of my things and put it on a CD so I can just get everything back into the new hard drive with all of my desktop settings, etc. saved?

you bet
[http://ubuntuforums.org/showthread.php?t=1607802](http://ubuntuforums.org/showthread.php?t=1607802)

---

### Post by asmoore82 on 2010-11-19
Big [SIZE="5"]+1[/SIZE] for clonezilla

---

### Post by d475719 on 2010-11-21
Thank you for your answers! Can you please tell me which option I would have to use to do this process from the clonezilla website? [http://clonezilla.org/clonezilla-live/doc/](http://clonezilla.org/clonezilla-live/doc/)

Do I follow the "Save disk image" instructions?

---

### Post by honeybear on 2010-11-21
easy : 

```
mkisofs -o mytarget.iso  file1 file2 folder1 ...
```

Enjoy the simple reply, no one told you that after 3-5 posts ...;)

---

### Post by The Cog on 2010-11-21
You asked about saving your desktop settings etc. These are contained in hidden directories (name starts with a dot) in your home directory. Many are in .config, but others are scattered in other hidden directories. 
To see the hidden directories, press Ctrl-H in your file browser.

Note that just copying files to a CD image burner will lose all the associated permissions and ownership for the files. You are better off making a tar archive and putting all the files in there. Then just put the tar archive on the CD as one big data file. When you unpack the tar archive you will find all the ownership and permissions preserved.

---

