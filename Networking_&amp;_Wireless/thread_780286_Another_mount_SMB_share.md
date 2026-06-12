---
title: "Another mount SMB share"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by xylith on 2008-05-03
Hi.

This is driving me nuts. I've tried lots of guides, and it still won' work!

I want the computer to automatically mount two windows shares on startup.

The names are "Giganten (D)" and "Lagring (E)". These shares are located on the computer with IP-adress 192.168.0.104.

I have created the folders "htpc_d_giganten" and "htpc_e_lagring" on the local computer, in the /mnt folder. Both have chmod 777 (just to eliminate any access failures...).


I put this in my /etc/fstab

> //192.168.0.104/Giganten\ \(D\) /mnt/htpc_d_giganten    smbfs   auto,username=htpc,password=lol,uid=marie,umask=000,user        0       0
//192.168.0.104/Lagring\ \(E\)  /mnt/htpc_e_lagring     smbfs   auto,username=htpc,password=lol,uid=marie,umask=000,user        0       0

sudo mount -a  output:
> [mntent]: line 12 in /etc/fstab is bad
[mntent]: line 13 in /etc/fstab is bad


This computer is running Hardy, the remote computer is running XP Media Center.

Thanks!

---

