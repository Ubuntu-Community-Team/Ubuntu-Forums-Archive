---
title: "delay boot until network is up?"
date: 2016-10-22
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2016-10-22
I'm not sure what I did, but I broke it. I installed a new router this weekend. In setting it up, I had to remove the network profile for the old router (long story) form my Ubuntu 16.04LTS laptop. I am auto-mouting a couple of network attached hard drives via fstab. It worked fine up until now. I can still mount the drives from the command line, but they are not auto-mounting at boot. I THINK it's because the system is booting up past fstab before the network is fully available. Can someone point me in the right direction? Thank you.

---

### Post by TheFu on 2016-10-24
Post the fstab file.
Have you considered using autofs which will only mount storage when it is requested? In theory, that wouldn't happen until some user action, well after boot is finished.

---

### Post by rebeltaz on 2016-10-29
I'm sorry.. I've been having trouble with my internet. Here is the fstab file:

```

derek@derek-home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a696e1aa-df8d-491c-8e39-f941d5538c40 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3554a897-5344-4980-bf71-843927577643 none            swap    sw              0       0


//192.168.1.15/multimedia	/mnt/multimedia	cifs	auto,uid=derek,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775	0	0

//192.168.1.15/shop.data	/mnt/shop.data	cifs	auto,uid=derek,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775	0	0

//192.168.1.15/shop_docs	/mnt/shop_docs	cifs	auto,uid=derek,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775	0	0

```

This worked fine with 10.04LTS but stopped when I "upgrade." autofs sounds ok... I am not familiar with that option.

---

### Post by TheFu on 2016-10-29
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

BTW, I thought uid and gid always needed to be numbers? That might be the quick fix.

---

### Post by rebeltaz on 2016-10-29
I don't know about name vs number.... I got that from here - [https://ubuntuforums.org/showthread.php?t=1806455](https://ubuntuforums.org/showthread.php?t=1806455) - and it worked so I went with it... I'll look at autofs but that looks a little more complicated that what I used to use :(

---

### Post by TheFu on 2016-10-29
a) Looks like you copied the wrong line. The correct option is probably (can't tell without seeing your passwd and group files):
```
uid=1000,gid=1000,
```

b) autofs is slightly more complicated, but does what you want. It really isn't THAT complicated.  Just 2 files to edit and you'll reuse the credentials file as is. It is used all over the world daily for all sorts of stuff and has been around longer than I've been using Unix.

---

### Post by rebeltaz on 2016-10-29
> **TheFu said:**
> a) Looks like you copied the wrong line. The correct option is probably (can't tell without seeing your passwd and group files):
```
uid=1000,gid=1000,
```

Yeah, I saw that in another similar page just now, so I tried that (after installing winbind) and still no good. 1000 is the correct number, so...

> **TheFu said:**
> b) autofs is slightly more complicated, but does what you want. It really isn't THAT complicated.  Just 2 files to edit and you'll reuse the credentials file as is. It is used all over the world daily for all sorts of stuff and has been around longer than I've been using Unix.

lol... I'll try it and see what happens. Thanks.

---

### Post by rebeltaz on 2016-10-30
I tend to make things more complicated than they actually are. After rereading that page, it's not so bad... 

I didn't see where to put the credentials file in the map file, but using this line: 

```
mntpoint -fstype=cifs,rw,username=myuser,password=mypass ://example.com/shrname
```

I was able to supply the username/password directly. It seems to be working great. Thank You!

---

