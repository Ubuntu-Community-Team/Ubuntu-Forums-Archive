---
title: "Can't connect to Windows shared printer"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Nano on 2007-07-16
I'm running a small network where I have a printer connected to a Windows Box.
This printer is shared and can be seen and connected to from all win machines but I can't from Ubuntu.
I do can see shared folders, etc.

When I try to connect to:
smb://192.168.2.88/Brother/ It asks for user and password and doesn't matter what I type it always fails.

What am I missing? 

Thanks guys

---

### Post by linuxwizard on 2007-07-16
These may help

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Nano on 2007-07-17
Thanks but I already saw that and didn't help.
My ubuntu box simply cannot see the shared printers.

From Nautilus it keeps asking for user/pass and no combination seems to work.
What am I doing wrong?

---

### Post by Nano on 2007-07-17
> 
smbclient -L 192.168.2.88 -U guest -W WORKGROUP
Password: 
Domain=[VENUS] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        print$          Disk      Printer Drivers
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Brother         Printer   Brother DCP-7010 USB
session request to 192.168.2.88 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[VENUS] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]


In other words, I can see it but I can't connect to it with any user/pass combo.

---

### Post by lsutiger on 2008-05-22
I have the same problem. Did you ever solve this problem?? 
I am in trying to connect to a printer that is attached to a computer that is logged onto a windows 2k3 domain.

---

