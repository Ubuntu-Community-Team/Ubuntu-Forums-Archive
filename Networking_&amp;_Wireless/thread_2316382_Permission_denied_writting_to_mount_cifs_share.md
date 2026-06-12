---
title: "Permission denied writting to mount cifs share"
date: 2016-03-07
forum: Networking &amp; Wireless
---

### Post by ijk2 on 2016-03-07
Hello everybody,

I have permission problems on my network share.

I have an hard drive plugged on my VirginBox (internet access provider router) that I have configured for sharing.

From a Windows computer, I can access and write to the drive through the following path : \\192.168.1.1\DD

From Ubuntu, I have full access from the path smb:\\192.168.1.1\DD
But, if I mount the drive, I can read everything on the drive, I can create new folders, but I can't create new files ! I have "permission denied" !

I can't understand why ! I am using the following command:
[COLOR=#000000][FONT=Arial]mount //192.168.1.1/DD mnt/test -o guest,sec=none,dir_mode=0777,file_mode=0777,iocharset=utf8,noperm -t cifs[/FONT][/COLOR]

I have the same problem from my Raspberry Pi 2 running Rasbian jessie.

It is probably a configuration problem but I tried many parameters without success to make it work correctly.


Does anyone can help me ?
Thanks

---

