---
title: "NIS ypbind"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by sigbert on 2008-05-09
Hi,

I'am running Ubunbtu 8.04 (64 bit). During startup ypbind is not able to find my NIS Server (SUN Solaris). However, when I log in after startup and restart ypbind, portmap and autofs then everything works fine. Any idea what goes wrong during startup?

Thanks Sigbert

---

### Post by isilmeraumo on 2008-05-12
The NetworkManager only activates your network once you login, meaning your computer does not have an IP address until after logging in.  The way I fix this is to login with the admin user I created during install and go into manual configuration for the NetworkManager and disable roaming mode and setup the wired connection to use dhcp.  After that, nis usually works.

---

### Post by bristleburger on 2008-07-05
Thanks for your posts guys!

I upgraded to Hardy yesterday and had the problem with NIS that you describe.

In may case I managed to get NIS working again by adding the following to /etc/rc.local: /etc/init.d/nis restart

---

### Post by fergus on 2008-07-27
add -no-dbus to /etc/default/nis YPBINDARGS to fix the problem

fergus

---

### Post by k1103 on 2008-07-28
> **fergus said:**
> add -no-dbus to /etc/default/nis YPBINDARGS to fix the problem

fergus, thanks a lot. That did it for me. You saved my day.

---

