---
title: "Windows 10 to Samba - Connecting port 80 instead of 445, but only once?"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by drketrnl43 on 2015-10-08
Hey there. This issue has been plaguing me for months now and have tried every solution I could find.

Samba server (4.1.6) runs on Ubuntu 14.04 LTS. For some reason, Windows 10 tries to connect on port 80 (WebDAV) instead of 445 (SMB), and I recieve a "network location cannot be reached" error. Strange thing is when I try it again immediately after, the connection works and I can browse files with no issue. I can restart the Win10 machine and try to connect, get the error, connect again, and everything's fine.

I ran Wireshark on the Win10 machine and indeed, it recieves the correct IP from the NetBIOS request but then immediately tries to connect on port 80. Connecting by "\\<IP address>" works fine, using "net view <IP address>" in the command prompt works as well and lists the shares. It's just using the File Explorer and either selecting the server in the Network list or using "\\<Machine name>."

The other strange thing is that my Windows 7, 8.1, and even other Ubuntu machines have no issues at all with connecting and browsing either way.

Here's a clip of my smb.conf with global and an example share in case that helps:

```

[global]
    server role = standalone server
    map to guest = Bad User
    passwd program = /usr/bin/passwd %u
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    load printers = No
    printcap name = /dev/null
    disable spoolss = Yes
    dns proxy = No
    panic action = /usr/share/samba/panic-action %d

[share]
    path = /storage/Applications
    read only = No
    create mask = 0775
    force create mode = 0775
    directory mask = 0775
    force directory mode = 0775
    inherit owner = Yes
    guest ok = Yes

```

Like I said, I have searched threads on other sites and their solutions did not work for me, and those were dealing with earlier Windows versions as well. If there's something I'm missing to support Win10 or if it's a known Win10/Samba issue, that'll put me at ease a bit more. Just wanna make sure I'm doing everything right.

Thanks!

---

