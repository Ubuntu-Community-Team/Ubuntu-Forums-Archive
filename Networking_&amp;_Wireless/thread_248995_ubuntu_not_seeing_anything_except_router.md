---
title: "ubuntu not seeing anything except router"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by donchiz on 2006-09-01
Hi all,
Ive just installed dapper version of ubuntu for AMD64.
Have connected it to a linksys WRT54G router and it is playing up. I can ping the router and access its settings, i can ping the cable modem and access its settings, however i can neither access the internet nor any other computers. Using Ping in networking tools allows ping for router/modem but when i try the known ip of another comp it doesnt even register having transmitted the packets!
Any ideas at all what is going on?
And any ideas why i cant access NTFS partitions as a normal user? i have to open nautilus as root. Sigh.
Many thanks

---

### Post by Uluen on 2006-09-02
[QUOTE=donchiz]Hi all,
Ive just installed dapper version of ubuntu for AMD64.
Have connected it to a linksys WRT54G router and it is playing up. I can ping the router and access its settings, i can ping the cable modem and access its settings, however i can neither access the internet nor any other computers. Using Ping in networking tools allows ping for router/modem but when i try the known ip of another comp it doesnt even register having transmitted the packets!
Any ideas at all what is going on?[/QUOTE]Is DHCP server enabled on the router and is your Ubuntu a DHCP client?
What's the output of ```
$ route
``` and ```
$ cat /etc/resolv.conf
```


[QUOTE=donchiz]And any ideas why i cant access NTFS partitions as a normal user? i have to open nautilus as root. Sigh.
Many thanks[/QUOTE]Try ```
$ sudo chown youruser /pathto/ntfsmount
```

---

### Post by sebastfr on 2006-09-02
About your 'mount' problem, from 'man mount':

> 
Mount options for ntfs
       iocharset=name
              Character set to use when returning file  names.   Unlike  VFAT,
              NTFS suppresses names that contain unconvertible characters.

       utf8   Use UTF-8 for converting file names.

       uni_xlate=[0|1|2]
              For  0  (or  `no'  or  `false'), do not use escape sequences for
              unknown Unicode characters.  For 1 (or `yes' or  `true')  or  2,
              use vfat-style 4-byte escape sequences starting with ":". Here 2
              give a little-endian encoding  and  1  a  byteswapped  bigendian
              encoding.

       posix=[0|1]
              If  enabled  (posix=1),  the  file  system distinguishes between
              upper and lower case. The 8.3 alias names are presented as  hard
              links instead of being suppressed.

       uid=value, gid=value and umask=value
              Set  the  file permission on the filesystem.  The umask value is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.


I think the last few lines explain your problem. just change your 'umask' settings when mounting your ntfs drive.

seb

---

