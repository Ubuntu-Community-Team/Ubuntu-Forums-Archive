---
title: "remote login same user that is loged in localy"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by adammw on 2007-08-25
Hi.
Is it possible to login remotely (via XDMCP) with the same user that is logged in locally?

---

### Post by thelinuxguy on 2007-08-25
Yes. You can login and run programs alright.
However, some applications such as NetBeans will run only from one of the logins at a time as the NetBeans work directory will be locked once it is started. With other applications that don't have this sort of protection, you may corrupt your files. But this hasn't happened with me yet.

---

