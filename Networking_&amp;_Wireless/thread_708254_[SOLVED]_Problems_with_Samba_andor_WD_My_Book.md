---
title: "[SOLVED] Problems with Samba and/or WD My Book"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by teerik on 2008-02-26
I'm trying to connect Western Digital's external HDD My Book World Edition with my Gutsy. It worked for months rather fine but all the sudden I can't mount a disk share. As far as I know I haven't changed a thing in my network.

First of all I can connect and list shares with smbclient:
```
$ smbclient -L mybookworld
Password: 
Domain=[MYBOOKWORLD] OS=[Unix] Server=[Samba 3.0.23c]

        Sharename       Type      Comment
        ---------       ----      -------
        SHARE           Disk      
        PUBLIC          Disk      
        IPC$            IPC       IPC Service (MyBookWorld)
Domain=[MYBOOKWORLD] OS=[Unix] Server=[Samba 3.0.23c]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        LEPPA                MYBOOKWORLD
```


But when I try to mount it I get an error (this exact command used to work few weeks ago):
```
$ sudo mount -t smbfs -o username=teerik //mybookworld/share /share
Password: 
24761: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```

Also when trying to use smbclient to access share I get an error:
```
$ smbclient -Uteerik //mybookworld/share
Password: 
Domain=[MYBOOKWORLD] OS=[Unix] Server=[Samba 3.0.23c]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```

Can someone help me to solve this problem? Is the HDD possibly broken or what can have happened? Share is listed with smbclient but otherwise it looks like it wouldn't exist at all.

---

### Post by meney on 2008-02-27
I am having a similar problem, except that I have to use the IP address. It won't accept mybookworld at all.

---

### Post by teerik on 2008-06-05
The hard disk inside the device was broken. Therefore I couldn't access it. I had to send it for data rescue to get anything out of there.

---

