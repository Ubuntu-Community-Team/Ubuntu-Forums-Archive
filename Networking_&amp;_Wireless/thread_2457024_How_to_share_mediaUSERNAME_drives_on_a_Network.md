---
title: "How to share /media/USERNAME/ drives on a Network"
date: 2021-01-24
forum: Networking &amp; Wireless
---

### Post by pegasomus on 2021-01-24
Hi there, I'm completely new to the platform. I'm running a Lubuntu installation with Samba server.
I've successfully managed to create user accounts, share folders and access them on my LAN.
I have four SATA disks I need to share as a backup destination, but the system keeps mounting them under the /media folder and there's no way to access them via the LAN.
I've read countless guides and tried everything via the Terminal.

How can I manage to let them be listed on the network? Any idea?
Thanks in advance

---

### Post by Morbius1 on 2021-01-24
> I have four SATA disks I need to share as a backup destination, but the  system keeps mounting them under the /media folder and there's no way to  access them via the LAN.
Are you sure it's mounting them under /media?

Once upon a time that was not a good idea because that is where the system mounts things. But it hasn't done that in a decade. The system now mounts things under /media/your-user-name. That is a problem since it only allows "your-user-name" access to what is under it.

If in fact it is under /media/your-user-name just change your mount point so that it points somewhere else - under /media directly will work.

 Or you can add to the [global] section of smb.conf a "force user = your-user-name" but then everything the client user will do would be as "your-user-name" which may be inconsistent with how you are doing backups.

---

### Post by pegasomus on 2021-01-24
Thanks Morbius1, I've already tried both solutions without success. Changing the mount point - say it, under /public/ - doesn't allow disks to popup. And the "force user" action, which I did under GAdmin, had no effect. I've also tried to change the home folder for specific users under GAdmin but I'm always getting error messages. That is very frustrating... should I completely give up and run FreeNAS instead?

---

### Post by Morbius1 on 2021-01-24
Gadmin? Are you talking about gadmin-samba?

That is one of your problems.

Please post the output of the following commands:
```
testparm -s
```
```
sudo blkid -c /dev/null
```
```
 cat /etc/fstab
```

If you are using gadmin-samba we need to restore the factory default version of smb.conf. Easy enough to do but I need to see the output of those commands first.

---

