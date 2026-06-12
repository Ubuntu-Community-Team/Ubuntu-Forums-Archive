---
title: "Network Shares - NASes, Ubuntu and Win 8"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by Ackis on 2014-01-18
Hello everyone, I've been having some strange issues lately.

My current set up is:
[LIST]
[*]DNS-323 NAS running alt-f
[*]ReadyNAS Duo v2
[*]Ubuntu Server 13.10 Headless
[*]Win 8.1 PC's
[/LIST]

This is my current "working" fstab:

```
# NAS Shares//192.168.0.102/media /media/READYNAS/ cifs credentials=/etc/smbcredentials,iocharset=utf8,sec=ntlm 0 0
//192.168.0.102/media2 /media/READYNAS2/ cifs credentials=/etc/smbcredentials,iocharset=utf8,sec=ntlm 0 0
//192.168.0.100/media /media/DNS-323/ cifs defaults,uid=997,gid=997,credentials=/etc/smbcredentials,iocharset=utf8,sec=ntlm 0 0

```

I changed the DNS-323 settings based off of this post here:
[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

My previous settings for the DNS-323 were identical to the READYNAS entries.  The issue with them was that it looked like only root could write to the DNS-323 whereas any of my service accounts were able to read/write to the READYNAS as needed.

Basically is, why do I need to connect to the DNS-323 as a specific user when I'm specifying appropriate credentials in the smbcredentials file?  (I have a media user that has access to the media portions of my NASes only, and on Ubuntu I'm trying to have all my services run with their own user account).

THank you.

---

### Post by Morbius1 on 2014-01-18
> Basically is, why do I need to connect to the DNS-323 as a specific user when I'm specifying appropriate credentials in the smbcredentials file?
You aren't.

You are connecting to the server with the user specified in the smbcredentials file.

You are specifying the ownership of the mouted share on the client when you use uid / gid.

---

### Post by Ackis on 2014-01-18
> **Morbius1 said:**
> You aren't.

You are connecting to the server with the user specified in the smbcredentials file.

You are specifying the ownership of the mouted share on the client when you use uid / gid.


Okay that makes some sense, but it seems contradictory to what I experienced.

When I connected to the drive with the first method, the mounted share was owned by either my user or by root.  The permissions for that share allowed global r/w access yet I still wasn't able to write anything.  Which part of the permission structure may have been causing this?  I'm essentially dealing with 4+ individual machines with their own accounts and trying to network them.  Two of the machines are NASes with their own special OSes and whatnot, one is the Ubuntu machine and the rest are Windows machines.

Windows -> Windows is easy (Live unified account)
Windows -> NASes are easy (Samba share on the NAS with username/permissions for folders and authentication whenever I need to access the share).
Windows -> Ubuntu is easy (Samba share again or scp depending on requirements)
It's the Ubuntu -> NASes that's throwing me for a loop, and probably NASes -> Ubuntu when I get to that stage of my set up.

---

