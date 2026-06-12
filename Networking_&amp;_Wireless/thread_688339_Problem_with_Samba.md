---
title: "Problem with Samba"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by saffolino on 2008-02-05
I run ubuntu 7.10 in my dekstop and the other pc has windows XP.The problem  is that from Ubuntu I can't open a video, or open a rar,.zip with qcomicbook.IF I copy it from windows to Ubuntu it works(eheh obviously), but I don't want to copy! Open files from windows to ubuntu it works fine, help pls ;_;

---

### Post by swerdna on 2008-02-05
> **saffolino said:**
> I run ubuntu 7.10 in my dekstop and the other pc has windows XP.The problem  is that from Ubuntu I can't open a video, or open a rar,.zip with qcomicbook.IF I copy it from windows to Ubuntu it works(eheh obviously), but I don't want to copy! Open files from windows to ubuntu it works fine, help pls ;_;

It should work if you mount the share as a cifs drive, just like the reverse from windows when you "map network drive". Should be able to use like this:
mount -t cifs -o username=someobody,password=something //servername/sharename /home/username/destination_folder

---

### Post by saffolino on 2008-02-06
Impossible to mount //192.168.1.2/ because it's protected from write, read too.What's wrong? (Thanks anyway ;)  )

---

### Post by swerdna on 2008-02-06
> **saffolino said:**
> Impossible to mount //192.168.1.2/ because it's protected from write, read too.What's wrong? (Thanks anyway ;)  )

This works for me exactly:
**sudo mount -t cifs //192.168.1.2/linuxshare /home/suzette/Public**
It then asks for the password for suzette in the samba user database on the server and mounts the share into Public on the client. So add the Linux owner of your shared folder to the samba user database on the server.
The permissions on folder linuxshare on the server are drwxrwxrwx, so yours should be too.
The permissions on folder Public on the client are drwxr-xr-x before the share mounts. And when the share does mount they automagically change to drwxrwxrwx because thay map through from the server.

How's that work??

Swerdna

---

### Post by saffolino on 2008-02-06
saffolino@saffolino:~$ sudo mount -t cifs //192.168.1.2/D$ /home/saffolino/Shared
mount: wrong fs type, bad option, bad superblock on //192.168.1.2/D$,
       missing codepage or helper program, or other error
       In alcuni casi si possono trovare informazioni utili in syslog. Provare
       ad esempio 'dmesg | tail'

Why? ;_;

---

### Post by swerdna on 2008-02-06
> **saffolino said:**
> saffolino@saffolino:~$ sudo mount -t cifs //192.168.1.2/D$ /home/saffolino/Shared
mount: wrong fs type, bad option, bad superblock on //192.168.1.2/D$,
       missing codepage or helper program, or other error
       In alcuni casi si possono trovare informazioni utili in syslog. Provare
       ad esempio 'dmesg | tail'

Why? ;_;

Out of my competency level here. I suspect your filesystem for windows. Restart windows pressing F8 key and select to start Safe Mode With Command Prompt. Log as Administrator and run program **chkdsk** to see if you have disk errors.

---

### Post by jetsam on 2008-02-06
That error message is so opaque, but it happens when you don't have smbfs installed and try to mount a cifs or smbfs share.  

Try 
```
sudo apt-get install smbfs
```
and then retry the mount command...

---

### Post by saffolino on 2008-02-07
OK guys, almost! 

```

saffolino@saffolino:~$ sudo mount -t cifs //192.168.1.2/D$ /home/saffolino/Shared
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

I entered the right password, but still it says permission denied. My login name is in the samba's list :|

OK DONE:

sudo mount -t cifs //192.168.1.2/D$ /home/saffolino/Shared -o username=mylogin,password=mypass

ALL OK! THANK YOU THANK YOU ;)

---

