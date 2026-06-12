---
title: "keyring/network manager"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by bneva on 2009-01-15
Hi, I just installed ubuntu and it asked me for a password for the keyring to connect to the internet.  I'm just wondering if there is a way to change this password, I'm very new to linux so I'm not sure of the commands.  I thought it was asking for the password for the wireless I was connecting to so I put that in and I'd prefer to change it if I could.  

Thanks!

---

### Post by anewguy on 2009-01-15
You can delete the keyring file and it will ask again at next boot/connect to the internet.  If you use your logon password, it won't prompt you for a password after that.

See this link:

[http://www.ubuntued.com/?p=15]("http://www.ubuntued.com/?p=15")


There is also supposedly a package in synaptic package manager called Seahorse which will let you change the password.  Just install the package from synaptic package manager and run it (I think it's still available for the latest releases, but I haven't checked and I'm on a Windows box right now).

Dave :)

---

### Post by bneva on 2009-01-20
hmm, I tried seahorse and deleted the key but it still wants the OLD password after restarting and trying to connect.

---

### Post by anewguy on 2009-01-20
Try this post for actually deleting the keyring file, then reboot - when it asks for a password for the keyring itself (not for a network connection) use your logon password and it won't ask for the password again.

[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/]("http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/")


Dave :)

---

