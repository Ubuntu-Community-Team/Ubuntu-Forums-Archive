---
title: "Mounting a Windows network share"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by TidySi on 2007-03-19
Im new to Ubuntu and pulling my hair out with this, I've read through many web pages and tried various recommendations but none seem to work.

Basically I have a MS Media Centre downstairs which controls my TV etc. its D drive is shared so that I can access it to drop movies on etc. Through Nautlius I can access the system, browse, read and write files by going to 'Places' > 'Connect to Server' and then adding in the details of my Windows box. However when I am in any application and want to access the network drive to access any files I cannot see the system.

I have tried adding a mount point into /etc/fstab and this does not work. I can see the mount within Nautilus but when I try to access it, it displays that only root can mount. 

This is the line I have put into /etc/fstab:
//192.168.1.101/data /media/mce smbfs username=xxx,password=xxx 0 0

This is the error I get:
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
FUSE mount point creation error: No such file or directory
Unmounting /dev/disk/by-uuid/12A85639A8561B93 (OS)
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
FUSE mount point creation error: No such file or directory
Unmounting /dev/disk/by-uuid/568062D18062B6E1 (Programs)
mount: wrong fs type, bad option, bad superblock on //192.168.1.101/data,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any help would be appreciated!

---

### Post by apjone on 2007-03-19
TO mount is manually, open a terminal and run
```

sudo apt-get install smbfs 

```
smbfs is the filesystem driver to allow mounting network shares

then run the following to mount the share

```

sudo smbmount //192.168.1.101/data /media/mce username=xxx,password=xxx,uid=username

```

This will mount it and give access to the user "username".

---

### Post by apjone on 2007-03-19
add the following above "exit 0" in /etc/rc.local if you want it to map at boot
```

/bin/bash smbmount //192.168.1.101/data /media/mce username=xxx,password=xxx,uid=username

```

---

### Post by TidySi on 2007-03-19
Thanks it worked, although did have an issue with some folder permissions with My Documents however used chmod and resolved this.

---

### Post by apjone on 2007-03-19
Great stuff.

---

### Post by dvessels on 2007-03-27
This may be same question, different form. Every time I try to use my upstairs ubuntu laptop to access my windows file storage XP machine, it asks me to logon to the WIndows machine and will not accept ANY authentication I offer. Since I installed both machines, I figured that one or another must work, but NONE does.

Does anyone have any ideas how to access an XP machine from an Ubuntu machine? The other direction works very well; I can access Ubuntu machines from other Ubuntu or XP machines. It's just accessing XP from Ubuntu that's driving me silly(er).:( 

THANKS!!

---

### Post by apjone on 2007-03-29
the username and password should be the one used to log on to the XP machine. eg
```

Username: nameofxpbox\username
password : ******password***

```

---

### Post by oalkatib on 2007-11-14
> **dvessels said:**
> This may be same question, different form. Every time I try to use my upstairs ubuntu laptop to access my windows file storage XP machine, it asks me to logon to the WIndows machine and will not accept ANY authentication I offer. Since I installed both machines, I figured that one or another must work, but NONE does.

Does anyone have any ideas how to access an XP machine from an Ubuntu machine? The other direction works very well; I can access Ubuntu machines from other Ubuntu or XP machines. It's just accessing XP from Ubuntu that's driving me silly(er).:( 

THANKS!!

I have the same problem. I have been All over the net for the passed 2 days trying to find out how to do it, HELP!!!!
Thanks!

---

### Post by stevux on 2007-11-14
I just replied to a similar thread this morning, and now stumbled upon this one, I will post the same hit I got from google. This article addresses 3 issues;

  1) how to mount smb shares
  2) how to automatically mount smb shares at startup
  3) how to automatically provide user/pass when mounting the share

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

btw; does anyone know why thisthread is marked 'cool' ?

hth,

---

