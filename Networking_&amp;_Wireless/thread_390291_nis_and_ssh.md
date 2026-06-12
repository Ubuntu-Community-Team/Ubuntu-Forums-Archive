---
title: "nis and ssh"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by paulroachhair on 2007-03-21
I'm having trouble with NIS and SSH. I can log in to my Ubuntu box with my NIS login, but I cannot SSH to my Ubuntu box with my NIS login. Only local users can SSH in. It says that my password is invalid when I try to log in. Where's the problem--SSH or NIS?

Thanks.

---

### Post by Mr. C. on 2007-03-21
What's the value of USENIS in :

/etc/sysconfig/authconfig

If no, change it to yes.

MrC

---

### Post by paulroachhair on 2007-03-22
Erm, I don't have /etc/sysconfig/authconfig. Does that mean I didn't install some package I need? (btw, I am using Edgy)

---

### Post by Mr. C. on 2007-03-22
Sorry, this file must have been a remnant from a previous install.  I cannot find it in any packages, and it appears to be RedHat!  Argh.


Have you done the steps provided here? :

[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

Some passwd and shadow are in "comat" mode, you need to add the + entries at the end of those files to cause NIS lookups to occur after the password file is checked.

MrC

---

