---
title: "samba and NTFS partitions"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by DemonDust on 2008-03-03
I've have a bit of trouble with samba. I have a Ubuntu linux 7.10 installation on my pc running as host for samba and a XP professional running in VMWare(the guest). Before i installed Ubuntu i had Windows on and i had 5 partitions. In the C drive i've put Linux and i am left with 4 NTFS partitions.
My problem is that i don't know how to configure samba so that i can share those partitions with VMWare.
I managed to configure samba for the files from the linux installation (great tutorial here [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/")), but when i share files from one of the NTFS partitions, windows gives me "network access not allowed" error.

---

### Post by Eiríkr on 2008-03-10
Well, I've never done this myself, but the first questions to ask are:
[list=1][*]Where are the NTFS partitions mounted in your Ubuntu filesystem?
[*]Can you post us your smb.conf file?[/list]
We can get started once we know a bit more about what's going on.  

Cheers,

Eiríkr

---

### Post by superprash2003 on 2008-03-10
follow the samba installation instructions here [http://ubuntuguide.org](http://ubuntuguide.org) .. and in your vmware setup.. go to the OS properties and select Bridged mode in the networking options.. now on your xp(vmware) open windows explorer and type \\(ubuntu computer name) or \\(ubuntu ip address).. this should work!!

---

