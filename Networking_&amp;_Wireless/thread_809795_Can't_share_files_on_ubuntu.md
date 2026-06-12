---
title: "Can't share files on ubuntu"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by imsorrisuck on 2008-05-27
I can access shared files from my xp no problem on Ubuntu. But today I tryed to share a  file in Ubuntu. Just My Pictures and another folder I made on desktop. It said it had to install some things so I let it. But then when I tryed to share the folder it said-

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


I am the administrator so I'm not sure what the problem is. If anyone knows what the problem is please reply. Oh i am running the latest version of Ubuntu.

---

### Post by jetsam on 2008-05-27
This is a known bug.  Post four of this thread has more details and the workaround:
[http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706")

Basically, log out and back in again or reboot after you install Samba and you should be able to share folders.

---

