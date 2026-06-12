---
title: "Lost Root Password"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by tachyon4 on 2009-05-11
how can i recover my lost root password? :(

---

### Post by Dr Small on 2009-05-11
Ubuntu doesn't have a root password. Use sudo, and your account password.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Iowan on 2009-05-11
Lose your [user password]("http://www.psychocats.net/ubuntu/resetpassword")?

---

### Post by Locutus_of_Borg on 2009-05-11
append "init=/bin/sh" minus the quotes onto the end of the kernel line in grub
boot that grub entry
upon booting enter "passwd" without quotes
enter new password
reboot

---

### Post by tachyon4 on 2009-05-13
oh. wow.

sudo is kinda nice.

thanks guys!

---

