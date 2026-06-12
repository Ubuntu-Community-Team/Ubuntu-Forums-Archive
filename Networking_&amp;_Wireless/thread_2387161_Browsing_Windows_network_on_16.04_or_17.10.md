---
title: "Browsing Windows network on 16.04 or 17.10"
date: 2018-03-15
forum: Networking &amp; Wireless
---

### Post by oregonbob on 2018-03-15
Ubuntu can't seem to get organised to make a fresh install just "work out of the box" in the simplest of cases. I just built a Ubuntu 16.04 and a Xubuntu 17.04 desktops and neither one can browse/open a simple Windows 10 workgroup/shares. They show up but if you click on them they just timeout (almost instantly).

Am I the only one that has this problem? Anyone have an idea?

---

### Post by Morbius1 on 2018-03-15
Wait until you see Ubuntu 18.04. You won't even be able to see your Windows machine. In an all Linux / macOS network however it's nearly perfect: [https://ubuntuforums.org/showthread.php?t=2384959](https://ubuntuforums.org/showthread.php?t=2384959)

Anyhoo, since it's Win10 we are talking about here open up a terminal and run this command with the ip address of the Windows machine:
```
smbclient -L 192.168.0.100
```
Do you get this error:
> protocol negotiation failed: NT_STATUS_CONNECTION_RESET
If you did it's because Win10 disabled SMB1 as a dialect and the Linux file manager uses smb1 by default.

You can fix that but then you won't be able to browse for Windows machines any more.

---

### Post by oregonbob on 2018-03-15
I turned on SMB 1.0 Server feature on Windows "Programs and Features" and now I can browse/access it all. Now I've got to see if I opened a security risk.

I ran your command and it returned: "The program 'smbclient' is currently not installed." Strange.
Then I installed smbclient, ran the command again and got, "WARNING: The "syslog" option is deprecated"
I'll quit and settle for SMB 1.0 server.
Update: Microsoft says don't use SMB1. It is dangerous. I'll have to figure out a better way. So little time...

Best solution: Do everything Morbius1 suggests in this post: [https://ubuntuforums.org/showthread.php?t=2384959](https://ubuntuforums.org/showthread.php?t=2384959)
After that I could browse everything without enabling SMBv1 on Windows 10 boxes.

---

### Post by Morbius1 on 2018-03-15
If you want to keep SMB1 disabled on WIn10 you can change how Linux access it by adding a line to  /etc/samba/smb.conf ( I would put it under the workgroup = WORKGROUP line ):
```
client max protocol = SMB3
```
Then save the file.

You will not be able to browse for the windows machine but you should be able to access it by name in Nautilus:
```
smb://Windows-Host-Name
```

---

### Post by oregonbob on 2018-03-15
Thanks Morbis1! I did everything you suggested here: [https://ubuntuforums.org/showthread.php?t=2384959](https://ubuntuforums.org/showthread.php?t=2384959)

And it all works perfectly even without SMBv1. I can browse all the Windows 10 boxes.

(This was done on a Xubuntu 17.10)

---

### Post by oregonbob on 2018-03-16
Tonight I built a VM of 18.04 Budgie Beta 1 and gave it a test drive. It browses Windows networks "Out of the Box"!

---

