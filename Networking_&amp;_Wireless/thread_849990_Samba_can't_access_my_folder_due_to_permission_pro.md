---
title: "Samba can't access my folder due to permission problems how do I fix? chmod."
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-07-05
Nautilus and Samba was working quite well for some time.  Now out of the blue all my shares are visible but I can not access them.  I get "folder contents could not be displayed"

So I check the samba logs and I find
>   '/home/steve/Installs' does not exist or permission denied when connecting to [Installs] Error was Permission denied
[2008/07/05 00:30:55, 0] smbd/service.c:make_connection_snum(1003)
  '/home/steve/VirtualBox' does not exist or permission denied when connecting to [VirtualBox] Error was Permission denied

I just tried to issue sudo chmod 777 VirtualBox

but nothing happend. 

How do I change this?  What group needs to have access to the folder in order to alow samba access?

It may be important to note that all of my shares are in my home directory, but those folders are symbolic links to files on another drive.  For example ~/VirtualBox is really /media/XXX/blah/VirtualBox.  Which folder becomes important to change permissions of?  Both?

---

### Post by superprash2003 on 2008-07-05
right click on the virtualbox folder and click on properties and go to permissions.. what are permissions shown?

---

### Post by Mysticle31 on 2008-07-05
Actually, I got it.

Somehow I was missing the guest = UID in the config flile.

Works Well Now

Although when I was looking at my permissions the owner of the VirtualBox folder was root and plugdev could read and write and others could do nothing.

What is plugdev?

How come if I tried to change the permission (as root) it woud "pop" back to the previous setting.  For example.  If I tried to set others to the UID or plugdev or whatever it would pop back to nothing as soon as I let go of the mouse button.  If I tried to change plugdev to the UID or anything.  Same thing.

---

### Post by superprash2003 on 2008-07-05
go to the terminal and type sudo nautilus and browse to the folder which you need to edit permission.. now it shouldnt pop back

---

