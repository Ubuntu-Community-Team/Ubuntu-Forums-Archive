---
title: "dns 323 stopped mounting - samba/cifs error 6"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by dlstrife on 2008-11-21
I've had a DNS 323 mounted to the filesystem with cifs and fstab for 6 months. the NAS has firmware version 1.05 and i'm running hardy 8.04. 

Lately I've been having issues where I get "Permission denied" issues when trying to unpack .rar files downloaded with the built-in bittorrent client on the NAS. These stick around a while then eventually go away with no explanation. 

Today my system stopped seeing the NAS. I can ping it, and I can access the admin website and FTP to it, but I cannot connect to it as a windows share or mount it. My XBOX still sees it too. I've tried tweaking the fstab line, mounting from the command line using smbmount, mount.cifs and mount commands. It previously gave me permissions error with mount error 13. I restored factory settings on the NAS and reset all the user privileges from the admin page. Now it gives me 

:~$ smbmount //140.180.129.69/Volume_1 /media/NAS -o user=dstrife,pass=XXXXX 0 0
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

It won't mount through nautilus "Connect to Server" method either, where it appears to be renaming Volume_1 to volume_1, which I can't seem to stop. I'm wondering if this is the same reason it won't mount with other methods as well. The share name Volume_1 is built into the NAS and I can't change it. 

I've had a friend try and connect to it as well from their Ubuntu Gutsy setup with the same results.

Anyone have any ideas?

---

### Post by dlstrife on 2008-11-24
Anyone? Any ideas? I've been working on this for days and no progress...

---

### Post by dlstrife on 2008-12-05
bump

I'm currently connecting as an ftp, which isn't optimal as most programs can't access files from it. anyone seen this before?

---

### Post by daveysan on 2008-12-30
Hi. I have had a few problems mapping directories from one Hardy desktop to another. I managed to solve my problem by ...

1. altering the /etc/samba/smb.conf file (Share definitions section) to allow access 
[homes]
    comment = Home Directories
    browseable = yes
    writable = yes
    valid users = %S


2. then using the command
sudo mount -t cifs //<remhost>/dave /home/dave/share -o username=<localmachine>/dave,password=<password>

This then allows me to access (with write permission) the entire contents of my account on the remote machine locally. Not the most secure of solutions,  but there is only me in my home office :D

Hope this helps ...

---

### Post by hashimoto on 2009-01-02
I just set up my DNS-323 (same fw) with the instructions provided here: 
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Everything was up and running with no problems at all, automounts during start-up.
Using 8.04.01.

---

