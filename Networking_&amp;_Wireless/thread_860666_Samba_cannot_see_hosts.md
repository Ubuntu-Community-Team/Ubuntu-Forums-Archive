---
title: "Samba cannot see hosts"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by infecticide on 2008-07-15
Hey all,

I have several machine connected behind a router, all of the machines can see each other in SAMBA except for the following scenario:

My SERVER (infecticide) is unable to see the FAMILY (WinXP) machine but it can see all the others.


Any ideas?

---

### Post by infecticide on 2008-07-17
I should clairify the information I entered above.

I cannot see the netbios name from my server but if I access it via IP address it works fine.




This is happening on AVATAR (KUBUNTU) trying to connect to FAMILY (WinXP)
How does this work?

infecticide@avatar:/mnt$ smbmount //family/OurPictures /mnt/family
mount error: could not find target server. TCP name family/OurPictures not found
No ip address specified and hostname not found
infecticide@avatar:/mnt$ smbclient -L family
Password: <enter>
Domain=[FAMILY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Default share
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        print$          Disk      Printer Drivers
        pictures        Disk
        hpphotos        Printer   hp photosmart 7150 series
        G$              Disk      Default share
        M$              Disk      Default share
        Temp            Disk
        F$              Disk      Default share
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        OurPictures     Disk
Domain=[FAMILY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
infecticide@avatar:/mnt$  



How the hell can samba see the family shares in one app but not in another?

---

