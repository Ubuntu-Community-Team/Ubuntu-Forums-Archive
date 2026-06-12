---
title: "[SOLVED] Mount on startup?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by HawkST on 2008-12-12
Hey guys, just installed 8.10 on my new machine, dual boot with XP as I have some programs I need to use for work that are Windows only, but if I am not using one of those programs, I tend to spend my time on Ubuntu.

Every time I login to Ubuntu I mount my Windows drive, so I can access some of the files on my XP partition. 

Is there any way to automate this so it happens every time I logon?

---

### Post by Locke_99GS on 2008-12-12
Add it's entry to your /etc/fstab file. You'll need to be super-user to do this, so:
```

sudo nano /etc/fstab

```

For example, you might mount a Windows partition like this:
```

/dev/sda1	/mnt/XP	ntfs	defaults	0	0

```

Of course, /dev/sda1 should be the location of the Windows partition, and /mnt/XP (or whatever mount point you want) is where it will mount to.

After you add that line, you can *mount -a* to mount it from the fstab, or leave it be and it will automatically mount at boottime.

---

### Post by Yugoo on 2008-12-12
Hi, it's very easy. You just need to write a startup script. Follow this link for detailed instructions

[http://ubuntu.wordpress.com/2005/09/...run-at-bootup/](http://ubuntu.wordpress.com/2005/09/...run-at-bootup/)

---

### Post by Duck2006 on 2008-12-12
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

