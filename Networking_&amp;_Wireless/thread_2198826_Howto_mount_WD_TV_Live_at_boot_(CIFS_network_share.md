---
title: "Howto mount WD TV Live at boot? (CIFS network share)"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by sberla54 on 2014-01-10
Hello guys,
i'm having a strange problem with my WD TV Live media player. The problem began some weeks ago; before, everything used to work great. I don't know what created the issue.

Anyway, this is the problem: i mount at boot the NTFS drive that is USB connected to the WD TV, as a common CIFS network drive, but it is owned by root.

That's really uncomfortable because i have to be root to copy my movies from the PC to the drive.
As i've said, until some weeks ago, with the same configuration, the network drive was owned by my user (sberla54) and i had no problem.

I use this string to mount, in /etc/fstab:

```

//192.168.31.69/WD_Elements_2TB_01                     /media/WDTV            cifs         username=username,password=password                0         0
```

I think that username and password are useless; i used to use "guest" for both and i can mount the drive anyway.

The folder /media/WDTV is owned by sberla54

Have you got any ideas?

---

### Post by TheFu on 2014-01-10
Look at **autofs**.  Be certain to use a credentials file that can be clearly protected. Not a good idea to have userids and passwords in files that must be readable by the world.

---

### Post by sberla54 on 2014-01-11
> **TheFu said:**
> Look at **autofs**. 
 

Never heard of it. I'm defenitely going to take a look at it.

> **TheFu said:**
> 
Be certain to use a credentials file that can be clearly protected. Not a good idea to have userids and passwords in files that must be readable by the world.

Even if username and password are "useless" for mounting the WD TV, i can't mount it without them. I think it's part of the way the device works.

---

### Post by TheFu on 2014-01-11
> **sberla54 said:**
> Never heard of it. I'm defenitely going to take a look at it.



Even if username and password are "useless" for mounting the WD TV, i can't mount it without them. I think it's part of the way the device works.

I have a WDTV live HD here. No credentials are needed, just the userid I want used for the mount. Perhaps mine is an older model?  Also, I haven't allowed any updates in over a year.  If it is working, I don't update. [http://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live](http://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live)

I stopped using the WDTV. Put in a silent XBMC/Linux box with GigE and never looked back.

---

### Post by sberla54 on 2014-01-18
Mine WD TV Live is [this one]("http://wdc.com/en/products/products.aspx?id=330"). Yours has a lot of developing and is really appreciated. Here you can find some modded ROM: [http://b-rad.cc/](http://b-rad.cc/)

Anyway, without credentials the drive can't be mounted and setting "sberla54" as username doesn't help.
Regarding updates, i think my problem could have been created form an automatic update...

---

### Post by sberla54 on 2014-03-16
I've found a solution [on _this post_]("http://community.wd.com/t5/WD-TV-Live-Hub-Network/mounting-WDTVLiveHub-on-linux/td-p/314623").

You have to configure fstab like this:

```
[COLOR=#003868][FONT=Arial]//device_ip/WDTVLiveHub  /path/to/mount cifs username=guest,password=,nounix,uid=server,gid=ser[/FONT][/COLOR][COLOR=#003868][FONT=Arial]ver,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/FONT][/COLOR]
```

So i've configured mine like this:

```
//192.168.31.69/WD_Elements_2TB_01                              /media/WDTV             cifs            username=guest,password=,nounix,uid=server,gid=server,rw,iocharset=utf8,file_mode=0777,dir_mode=0777                            0    0
```

and now everything works fine.

---

### Post by Keith_Beef on 2014-03-18
I've got a similar problem.

I have a ReadyNAS with my music on it, and I want to play it through Clementine which requires the NAS share to be mounted in the computer's filesystem.

So, I have two computers. On one of them, the mount works just fine. On the second, this is not working…

Computer one has this like in /etc/fstab
```
//nas-0x-xx-xx.local/media/Music        /mnt/NAS_music  cifs    guest,uid=1000,iocharset=utf8   0 0
```

So, following the instructions [here](https://wiki.ubuntu.com/MountWindowsSharesPermanently), I installed cifs-utils on computer two and added the same line to its /etc/fstab.

But when I try to (re)mount all the filesystems, I get this message:
```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I've discovered that there is a difference between the two computers… well, I knew they were running slightly different versions of Ubuntu, 

Computer one, where mounting the CIFS share works.
```
modinfo cifs
filename:       /lib/modules/3.2.0-59-generic/kernel/fs/cifs/cifs.ko
version:        1.76
description:    VFS to access servers complying with the SNIA CIFS Specification e.g. Samba and Windows
license:        GPL
author:         Steve French <sfrench@us.ibm.com>
srcversion:     9435BBC2F61D29F06643803
depends:        
intree:         Y
vermagic:       3.2.0-59-generic SMP mod_unload modversions 
parm:           CIFSMaxBufSize:Network buffer size (not including header). Default: 16384 Range: 8192 to 130048 (int)
parm:           cifs_min_rcv:Network buffers in pool. Default: 4 Range: 1 to 64 (int)
parm:           cifs_min_small:Small network buffers in pool. Default: 30 Range: 2 to 256 (int)
parm:           cifs_max_pending:Simultaneous requests to server. Default: 32767 Range: 2 to 32767. (int)
parm:           echo_retries:Number of echo attempts before giving up and reconnecting server. Default: 5. 0 means never reconnect. (ushort)
parm:           enable_oplocks:Enable or disable oplocks (bool). Default:y/Y/1 (bool)
```

Computer two, where it does not work:
```
modinfo cifs
filename:       /lib/modules/3.8.0-35-generic/kernel/fs/cifs/cifs.ko
version:        2.0
description:    VFS to access servers complying with the SNIA CIFS Specification e.g. Samba and Windows
license:        GPL
author:         Steve French <sfrench@us.ibm.com>
srcversion:     165364BB1DC2EA8E8A6FD42
depends:        fscache
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 686 
parm:           CIFSMaxBufSize:Network buffer size (not including header). Default: 16384 Range: 8192 to 130048 (uint)
parm:           cifs_min_rcv:Network buffers in pool. Default: 4 Range: 1 to 64 (uint)
parm:           cifs_min_small:Small network buffers in pool. Default: 30 Range: 2 to 256 (uint)
parm:           cifs_max_pending:Simultaneous requests to server. Default: 32767 Range: 2 to 32767. (uint)
parm:           enable_oplocks:Enable or disable oplocks. Default: y/Y/1 (bool)
```

AHA!

[This thread](https://bbs.archlinux.org/viewtopic.php?id=160047) on archlinux gave me the answer.

I was correct in suspecting that the cause was the difference between v 1.76 of CIFS for kernel 3.2 (where cifs mount has been working) and v 2.0 for kernel 3.8.

Now that I have added the option sec=ntlm to the entry in fstab I can mount the CIFS share.
Here's the line in fstab, now.
```
//nas-0x-xx-xx.local/media/Music        /mnt/NAS_music  cifs    guest,uid=1000,sec=ntlm,iocharset=utf8   0 0
```

---

