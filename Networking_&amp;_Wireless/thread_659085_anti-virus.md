---
title: "anti-virus"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by jhvillegas2 on 2008-01-05
I am looking for a good anti-virus program out there and how to install it.  Could anyone help me on this, please?

Thanks in advance.

jhvillegas2

---

### Post by jshein on 2008-01-05
Try installing avscan. It is a GTK front end for the popular clam antivirus engine.

You can install it with the following:

$ sudo apt-get install avscan

---

### Post by jhvillegas2 on 2008-01-05
Does avscan run automatically in the background upon startup, or do I have to start it manually?

---

### Post by Steveway on 2008-01-05
You don't need Antivirus on a normal Linux system.
If you want to run a mail-server then it is advisable but on a normal system you don't need it.

---

### Post by TheWizzard on 2008-01-05
> **jhvillegas2 said:**
> Does avscan run automatically in the background upon startup, or do I have to start it manually?

there are two types of anti-virus: 1) scanning hard drives, and 2) monitoring files and emails that are downloaded, etc. for the latter you'll need the clamav-deamon. 

```
sudo aptitude install clamav-daemon
```

---

