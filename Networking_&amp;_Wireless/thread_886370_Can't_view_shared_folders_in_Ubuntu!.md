---
title: "Can't view shared folders in Ubuntu!"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by cablejimmy on 2008-08-11
I have shared folders on my Ubuntu desktop that I cannot view on my Ubuntu laptop, which is on the same network!

---

### Post by Iowan on 2008-08-11
Desktop has Samba-server installed? Laptop user has account on desktop AND Samba?  Firewall on desktop? Can machines ping each other?

---

### Post by cablejimmy on 2008-08-11
Yes, both have samba & there's no firewall on either (I have apparmor, though). How would I tell if they could ping each other? If it helps, I can access my shared folders just fine when I boot into Windows XP on the laptop.

---

### Post by cablejimmy on 2008-08-11
Yes I had the computers ping each others' IPs, and it worked perfectly.

---

### Post by Iowan on 2008-08-12
On the terminal on the desktop:```
ps ax |mbd 
```
Should return something like```
 5036 ?        Ss     1:20 /usr/sbin/nmbd -D
 5038 ?        Ss     0:00 /usr/sbin/smbd -D
 5044 ?        S      0:00 /usr/sbin/smbd -D
11534 pts/0    S+     0:00 grep mbd

```OOPS - never mind... Working from Windows pretty much answers the question as to whether the server is running.

> **superprash2003 said:**
> to access windows shares from ubuntu go to terminal and type nautilus smb://x.x.x.x whre x.x.x.x is the ip of the windows machine...

---

### Post by cablejimmy on 2008-08-24
It works, but for some reason I can't do anything with the files. I can look at them, but I can't cut, copy, or even open any of the files.

---

### Post by bab1 on 2008-08-24
Each host needs to have the samba client installed too.  Add the smbfs client:```
sudo apt-get install smbfs
```  Then use Places>>Network to browse.

---

