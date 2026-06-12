---
title: "Mounting smb share for Buffalo Tera Station"
date: 2022-12-27
forum: Networking &amp; Wireless
---

### Post by janvi2 on 2022-12-27
We have a Buffalo Tera Station what we mount using Nautilus "Other Locations"-"Connect to Server". 
Obviously this uses GVFS and the complete path substitution looks like this:
/run/user/1000/gvfs/smb-share:server=10.10.20.18,share=data18/jv/job/file.ext

Unfortunately, some applications (not all) have problems with gvfs or temp files accessing the smb: share. 
Therefore I installed cifs and inserted the following into /etc/fstab:

//10.10.20.18/data18    /media/netshare cifs    username=nas,password=nothing,      uid=1000        0       0

The whitespace between were edited as TAB characters. This is the last line of fstab followed by a crlf

If I try to mount the share, the line is not accepted:

jv@JamesWebb:/etc$ sudo mount -a
mount: /etc/fstab: parse error at line 11 -- ignored
jv@JamesWebb:/etc$ 

Any hints for my wrong syntax ?
I am aware to put a strong password to ~/.smbcredentials as soon as it works

---

### Post by janvi2 on 2022-12-28
Ok, I played around a bit and the paramter vers=2.0 is doing the trick for my hardware:

>sudo mount -t cifs //10.10.20.18/data18 /media/netshare -o  username=nas,password=nothing,uid=1000,vers=2.0

---

