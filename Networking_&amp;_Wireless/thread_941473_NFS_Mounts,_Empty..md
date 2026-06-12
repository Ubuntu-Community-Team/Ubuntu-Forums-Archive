---
title: "NFS Mounts, Empty."
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by nemodx on 2008-10-08
Hi there, Sorry if this is the wrong section, and also if this has been discussed before and solved. In this case, please point me to the thread so I can get a fix for it.

Let me begin with my setup:

Debian Server (Lenny, but it works the same on Etch and Ubuntu Server, so that should not be the problem)


I have a directory which is called fileshare and in this directory I have a couple of subdirs which has multiple drives mounted to them.

/fileshare
/fileshare/movies/ (/dev/hdb1)
/fileshare/musik/ (/dev/hdc1)
/fileshare/photos/ (/dev/hdd1)

Now, I have tried multiple things in my /etc/exports:

/fileshare 192.168.1.1/24(rw,no_root_squash,subtree_check,async)

The above will not let me access the sub directories, so then I tried:

/fileshare/movies 192.168.1.1/24(rw,no_root_squash,subtree_check,async)
/fileshare/musik 192.168.1.1/24(rw,no_root_squash,subtree_check,async)
/fileshare/photos 192.168.1.1/24(rw,no_root_squash,subtree_check,async)

however, then I have to make 3 different entries on my client, which is kind of what i did NOT want.

so I made it look like this instead:
/fileshare/ 192.168.1.1/24(rw,no_root_squash,subtree_check,async)
/fileshare/movies 192.168.1.1/24(rw,no_root_squash,subtree_check,async)
/fileshare/musik 192.168.1.1/24(rw,no_root_squash,subtree_check,async)
/fileshare/photos 192.168.1.1/24(rw,no_root_squash,subtree_check,async)

and then again, I can see the subdirs/mounts, but not able to browse them.

The above is just an example, and I have FAR many more partitions mounted. (Using this for musik/video editing).

Does anyone know how I can access ALL subdirs from the root dir, and make it look like one share instead of having to mount around 30 dirs (looks messy, and it is messy hehe)

Client side: (Ubuntu Hardy, also tried with Debian, no luck on either)

Thank you very much in advance for your help!

Kind regards,

Nemo

---

### Post by jmbargar on 2008-10-08
It's quite simple. Just edit your /etc/exports and type something like this:

> / private_client_ip(rw,no_root_squash)

and just it. Don't forget you must restart your NFS server typing in a terminal:

> /etc/init.d/nfs-kernel-server restart

Good luck!

---

### Post by nemodx on 2008-10-08
Thank you, but that is not really what I want. :)

---

### Post by superprash2003 on 2008-10-08
which filesystem are the drives using? this is the line i use
/sharedir *(rw,async)

---

