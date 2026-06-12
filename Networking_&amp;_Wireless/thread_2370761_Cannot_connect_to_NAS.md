---
title: "Cannot connect to NAS"
date: 2017-09-06
forum: Networking &amp; Wireless
---

### Post by dhavalbbhatt2 on 2017-09-06
Hello all,
Coming back to using Ubuntu after a long time and running into some challenges. I have a NAS (QNAP 4-bay TS-469L) that I wold like to automatically connect while logging in/startup. The NAS is on the network (as compared to USB connected to the computer). I tried following the method prescribed [here]("http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/"), but that does not work for me. I get an error - "mount error (95): Operation not supported". Please let me know what am I doing wrong. Here is my fstab entry:"//10.0.0.9/Multimedia /media/Multimedia cifs credentials=/home/dhaval/.smbcredentials,uid=1000,gid=1000,file_mode=0777,dir_mode=0777,iocharset=utf8,sec=ntlm 0 0"

I have made some changes to the fstab entry from what was described in the link (especially added the sec=ntlm part) after reading some comments, but that has not helped as well. At this point, I am at a complete loss as to what might be wrong. 

I am not sure if this is a permissions issue or just the fact that I can't use cifs. 

I did try connect from CLI using the following command: sudo mount -t cifs -o username=[USERNAME] //10.0.0.9/Multimedia /media/Multimedia, however, for that I receive the same error message. 

Hoping someone can help. This is really hampering me get my work done.

Sorry, should have added my Ubuntu version:
Ubuntu GNOME 17.04 kernel 4.13

Thanks,
Dhaval

---

### Post by TheFu on 2017-09-07
If you can, use NFS, not CIFS.  NFS supports native file permissions and is faster than CIFS.  [https://wiki.qnap.com/wiki/Mounting_NFS](https://wiki.qnap.com/wiki/Mounting_NFS)

Mount points must already exist and it is usually best if they are empty directories.  You probably want the fstab "options" and be careful about extra spaces between options. Those aren't allowed.

This is wrong:
```
d ir_mode=0777,
```
The extra space breaks it.

Please use code tags (adv reply #) when posting code and output.  Makes life easier for us.

---

