---
title: "Problem with share on a NAS"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by WakkiTabakki on 2006-12-30
I have a problem with mounting a share on my WD Netcenter, which apart from the problem below is absolutely fantastic! 

The Netcenter is (apparently) running Linux kernel 2.4 with Samba 3.0.2.

I use cifs to mount a public share on it, and it does mount fine. I can access and modify the files on it, but anything I create from my linux computer becomes read-only!
All files created on the share are owned by uid 35001 and gid 40000 (or something like it). Anything created from windows all get permissons set to 777, but from linux they're 755 (and I'm not the owner!). Meaning that, if I try to copy a folder from linux to the share, the root folder gets created ok, but I'm not allowed to write in that folder... 

Ok, thats annoying and all, but here's the really weird part: 
If I create a folder using nautilus and try to remove it again, I get a permission denied error (which is completely logical, 'course), but if I bring up a terminal an do an 'rmdir' it doesn't fail, and it does remove the folder alright!!!

This is the entry in my fstab:
> //Netcenter/TheShare /mnt/Netcenter cifs credentials=/root/.NetcenterCreds,user,uid=1000,gid=1000,iocharset=utf8,file_mode=0666,dir_mode=0777,rw 0 0

What I could do is create a group on my computer with the same gid as the default owner on my netcenter and assign all users to that group, but still all files/folders are created with write-permission only on the owner. And also, it seems that file_mode and dir_mode are completely ignored...

My computer is running Edgy with 
Kernel: Linux Lap-Lin 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
Samba: 3.0.22

Any suggestions?

Cheers 
/N

---

### Post by kaarel on 2007-04-10
Does anyone have a fix for this? I have the exact same problem. Like when I make a new directory I cannot put files in it. I can only put files in existing dir and then the files get read only for me. However using smbclient works FLAWLESSLY. So now when I need to put things on the network drive I use smbclient and for reading I use mounted drive because it is much more convenient than the smbclient. Anyone knows how to make mounting a netcenter work?

---

### Post by kaarel on 2007-04-24
I just wanted to report that upgrading to Feisty (probably the updated samba client) seemed to solve the problem for me. I didn't try this in Edgy but adding *noperm* option made the day in Feisty. By the way *dir_mode* and *file_mode* options don't seem to have ANY effect at all no matter what other options I tried. Now all my directories and files are created as user 35007 and group 42000...whatever as long as it works :) However there are some files that have owner 35001 which I can read but I cannot delete while mounted nor while connecting with smbclient nor can I change ACL rules with smbcacls :( These files were probably created from a Windows machine but I can't delete them even from my XP account :( Anyone knows a fix?

Anyway this is my relevant /etc/fstab line:

```
//server/share /media/netcenter cifs defaults,noperm,noacl,iocharset=utf8,auto,rw,credentials=/my_credentials 0 0
```

---

### Post by Bubbel on 2007-07-24
Hi,

Had similar problems. I want to use the ACLs in CIFS, but that's for later concern.
If you would like the CIFS share to be used only with Linux Auth, i.e. no ACLs etc., you should use the following command (as root):

```
modprobe cifs
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
```

This must be run before any mount, so I suggest the noauto option in your fstab entries and place the lines above in your /etc/rc.local file, together with the actual mounts of all the CIFS shares.

CIFS now talks as it would against a WIN9x machine, concerning the security. I.E. it assumes no security. So you can set it yourself with file_mask, dir_mask, uid and gid.

My holy grail would be to fully use the ACL features in CIFS, but that takes some figuring out, I guess...

Good luck, Bubbels :-?

---

### Post by dodgeman79 on 2007-08-28
i just found this in a similar thread and it works great, it even discusses folder permissions.

[http://www.nomachetejuggling.com/2007/01/13/using-western-digital-netcenter-with-ubuntu-linux/](http://www.nomachetejuggling.com/2007/01/13/using-western-digital-netcenter-with-ubuntu-linux/)

---

### Post by WakkiTabakki on 2007-10-16
> **kaarel said:**
> I didn't try this in Edgy but adding *noperm* option made the day in Feisty

Was still having the same problem on Feisty, all tribes of Gutsy including the RC (which I'm currently on), and had forgotten all about this thread...

So, Kaarel, I tried the tip and lo-and-behold! It solved it! 
I love you :popcorn: 


/N

---

### Post by dodgeman79 on 2007-11-27
```

user@ubuntu:~$ sudo mount -t nfs 192.168.0.102:/shared/Main/ /home/user/shared
[sudo] password for user:
mount: wrong fs type, bad option, bad superblock on 192.168.0.102:/shared/Main/,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

can anyone give me some guidance?  I've made sure my netcenter is using nfs and it's still not working.

---

### Post by Bubbel on 2007-11-27
Well, this is off topic, bit do you have nfs-common installed?
if not, do the following:
sudo apt-get install nfs-common

and be aware files & dirs are case sensitive.

Goot luck, Bubbel

---

