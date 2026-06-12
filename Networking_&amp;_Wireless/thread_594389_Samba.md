---
title: "Samba"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by rafabarr on 2007-10-27
I installed Ubuntu 7.1 with zd1211usb wireless  and it works. I can access Internet wireless, vew and transfer files from other Windos XP computers network to Ubuntu. The Ubuntu computer appears in windows network with rest of computers in network, but when I try to access Ubuntu from Windows computer, a window pops up requiirng username and password for Ubuntu. When I write Ubuntus's username and password, it doesn't take it. Everything is perfect except this. Something can be done? Have been trying for hours with no result...
Thanks.
Rafael.

---

### Post by dkw on 2007-10-28
Hi Rafabarr,

You need to actually assign your user a samba password, you can do this using:

sudo smbpasswd -a username

-dkw.

---

### Post by nqsonk9 on 2007-10-28
Then restart your samba to make everythings perfect :D
sudo /etc/init.d/samba restart

---

