---
title: "Feisty: Samba problem"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by DJ_Cyberdance on 2007-05-21
Hi!

I am running Feisty and face the following problem. While remote access to samba shares works fine via the "Places => Network" menu, I cannot mount samba shares. In fact, the mount command succeeds and I can access files on the share but either immediately or after several minutes the mounted share is gone. When accessing the mount point on the console via cd /mount/point the console window hangs, there is no response at all.

I have also tried mounting the samba shares via fstab and a credential file which has the same effect.
dmesg shows the following messages:

[33813.319115] smb_proc_readdir_long: error=-13, breaking
[33881.368059] smb_proc_readdir_long: error=-13, breaking

and on shutdown there is a message saying

smb_retry: No connection process

Even tab completion does not work on the mount point anymore. When I try to complete /mount/poi by pressing the tab key, the terminal window hangs.   

On these shares are directories that contain many files. All programs accessing these directories take a very long time to retrieve the directory contents. While from Windows these shares can be accessed within about 5 seconds, this takes much longer from Linux applications. 

Note that smb server and client are connected via an GBit ethernet link. The server is running Debian and smbd Version 3.0.24. Before upgrading to Feisty I have used Debian on the client computer as well where mounting samba shares has not been a problem until now.

Any suggestions what I should try next?

Edit: This is the command I use for mounting samba shares as root:
mount -o username=user,uid=user //aaa.bbb.ccc.ddd/share /mount/point

---

### Post by Mujaheiden on 2007-05-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/15451](https://bugs.launchpad.net/bugs/15451) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, I have it too.

For a brief moment I was able to mount the samba shares which are on a Apache/2.0.54 (Mandriva Linux/PREFORK-13mdk) server but then suddenly my mount points [ get screwed up ]("http://ubuntuforums.org/showthread.php?t=452359"), but reaping them doesnt give a fix.

Now, whenever I use the fstab connection, or manually connect the shares, everything somehow related to the samba share gets to be totally slow (for example, the Desktop, because of a share shortcut on the desktop), not allowing me access.

However, I can just browse the network to the shares. But My Ubuntu doesn't work well with remote files, so I want to mount them as local.

FYI, these are the fstab lines, but i think they are correct;
```
//file\040server/User_folders /mnt/file_server smb defaults	0	0
//webserver/site /mnt/website smb defaults	0	0
```

---

### Post by Mujaheiden on 2007-05-24
darn, i mean

```
//webserver/site /mnt/website smbfs dmask=777,username=,password=	0 0
//file\040server/User_folders /mnt/file_server smbfs/mnt/file_server smbfs dmask=777,username=,password=	0 0
```

and ofcourse now it works

---

