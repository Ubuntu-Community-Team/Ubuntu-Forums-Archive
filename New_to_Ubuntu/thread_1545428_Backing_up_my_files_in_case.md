---
title: "Backing up my files in case"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by technmom on 2010-08-03
I have a dual boot system with Windows XP and Ubuntu 10.04. I have a terrible infection on the Windows side and am not sure how to back up the stuff I've done in Ubuntu. I suppose all I need to do is back up my user files and I can get back to this as soon as I fix Windows. Is there some way of looking for the infection while in Ubuntu since it is working? should I take this question somewhere else. I'd rather not have to uninstall everything, but am at a loss. Nothing works on the Windows side.

---

### Post by nhasian on 2010-08-03
all of your personal files are located in /home so it is easy to backup just by copying to a flash drive or external hard disk.  you can also scan the windows partition for viruses (virii?) while in ubuntu by installing a virus scanner such as [clam]("apt:clamtk")

```
sudo apt-get insall clamtk
```

---

### Post by technmom on 2010-08-03
thank you I will try that

---

### Post by technmom on 2010-08-03
clamtk seems cumbersome. From what I can see I can only scan one directory at a time

---

### Post by David Andersson on 2010-08-04
> **technmom said:**
> clamtk seems cumbersome. From what I can see I can only scan one directory at a time

When I tried it, as I recall, I only had to give it one directory name and it scanned the whole directory tree.

---

### Post by nhasian on 2010-08-04
yes you should be able to scan the entire windows drive in one shot.  it will most likely take several hours but such is life.

---

### Post by justin43384 on 2010-08-04
Simple Backup Config in the Ubuntu software center works too

---

