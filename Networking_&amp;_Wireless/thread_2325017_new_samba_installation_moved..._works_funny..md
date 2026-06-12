---
title: "new samba installation moved... works funny."
date: 2016-05-18
forum: Networking &amp; Wireless
---

### Post by kdxensen on 2016-05-18
Problems started when samba update broke file sharing. Finally removed samba to start over... sudo apt-get remove, sudo apt-get purge, sudo apt-get clean, sudo apt-get auto remove, and then manually deleted /etc/samba. Reinstalled. Now samba is in /usr/share/samba and doesn't seem to work right... It will see some windows 7 shares, not all; and windows doesn't see samba shares. Arrgh!!

Ubuntu 14.04

---

### Post by kdxensen on 2016-05-18
Turns out it's not really in /usr/share/samba... I haven't found it yet... Can't find smb.conf!

---

### Post by bab1 on 2016-05-19
> **kdxensen said:**
> Turns out it's not really in /usr/share/samba... I haven't found it yet... Can't find smb.conf!The Samba file sharing configuration files are always at /etc/samba/smb.conf.   If you deleted the smb.conf flie you need to add it back.  It should be enough to just copy the file at /usr/share/samba/smb.conf to /etc/samba/smb.conf and add your shares at the bottom for it to work.

The /etc/samba/smb.conf file is in the *samba=common *package I believe.  The other file that belongs in the /etc/samba directory is */etc/samba/gdbcommands* and you should have a directory named */etc/samba/tls*.

You can check to see if that package is install with this command```
dpkg -l samba-common
```
This is what you should get if the package is installed```
dpkg -l samba-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version        Architecture   Description
+++-===================-==============-==============-===========================================
**[COLOR="#FF0000"]ii[/COLOR] ** samba-common        2:4.3.9+dfsg-0 all            common files used by both the Samba server 
bruce@maui:~$ 

```The part listed in red means the package is installed.

---

