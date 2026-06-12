---
title: "Cannot conect to windows xp pro box"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by thejem on 2007-05-09
The first time I installed Ubuntu Edgy Eft I had internet access and could access my local network.
Then I did the upgrade to Feisty over the internet and had access to both also, but had some other problems which in the process of trying to fix I messed it up where it would no longer boot. Downloaded the CD file and wrote it thru Windows. Installed anew and all works except access to my windows shares. Tried to reinstall Edgy Eft again with the same result. Then tried Feisty again. Same. Have tried all i can find on forums but nothing works. I go to Places- Network and get Windows Network click that get Workgroup click that and get "The folder contents could not be displayed", "Sorry, couldn't display all the contents of "Windows Network:workgroup"
Help! Help! 
Finally got Edgy to show all the computers on the workgroup but still cannot see the shares.
if I type in smbclient -NL intel28 (name of windows box)
I get after a minutes wait,
timeout connecting to 208.67.219.130:445
timeout connecting to 208.67.219.130:139
Error connecting to 208.67.219.130 (Operation already in progress)
Connection to intel28 failed
if I type in smbclient -NL 192.168.102 (ip of windows box) 
I immediately get
Domain=[INTEL28] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Default share
        My Documents    Disk      
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        E               Disk      
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
session request to 192.168.0.102 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[INTEL28] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
Someone please help

---

