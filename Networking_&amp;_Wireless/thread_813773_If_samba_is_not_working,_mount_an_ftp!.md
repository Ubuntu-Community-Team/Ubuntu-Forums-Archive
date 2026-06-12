---
title: "If samba is not working, mount an ftp!"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by tigrezno on 2008-05-31
This is my advice, and it can be browseable from any OS. It's not samba, i know, but it is the same functionality.

I won't install samba again since vsftp is working very nice on my server.
My father can upload/download files from his windows file explorer like any other folder.

Nautilus supports it too, so at the end it feels the same.

If you don't have a big network, it's a possible solution IMO.

---

### Post by Healey on 2008-05-31
Hi
Yes I agree with you 

I used this in Fiesty - (Iam assuming that this is similar to your discussion)
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

I am yet to try it in Hardy as I am still dealing with other issues

My only concern is - does using vsftpd (Very Secure FTP Daemon) cause a security risk ???

I have read some info that sugests it may be a security risk, but I am still a newbie so I am hoping for comments from the experts

Thanks

---

### Post by tigrezno on 2008-05-31
well, i don't know if "very secure ftpd" isn't secure (its name should mean something), but i'm using it with user authentication in my home network on a server that isn't visible to the internet.

---

### Post by Healey on 2008-05-31
Hi

I just wondered - As I dont know much about it myself I thought I would ask

Regards

Healey

---

### Post by tigrezno on 2008-05-31
the only security risk that you might have, comes when using chroot_local_users = YES

i read about it on the vsftpd FAQ site.

In my server, i have that option set to "NO" (they can see everything, but can't modify anything but their home)

---

### Post by Healey on 2008-05-31
Hi

Thanks for that tip

As soon as I get the chance I will install it on my network

Regards

Healey

---

