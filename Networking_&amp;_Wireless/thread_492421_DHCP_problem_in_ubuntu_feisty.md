---
title: "DHCP problem in ubuntu feisty"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by aredoble on 2007-07-04
My ubuntu feisty desktop can not connect to the DHCP server, can not get an IP when using user (not root) account. but when I boot using recovery mode, login as root DHCP works fine. What is the problem?

---

### Post by ubuntu.daemon on 2007-07-04
thats really wierd, jus sounds lke your user doesnt have proper permission to connect to the dhcp server, when you log in like regular, try a
sudo /etc/init.d/networking restart
see if you get an ip. if that doesnt work set up a root account which i think u have
user@home: sudo passwd root
new unix password: password1
retype new password: password1
user@home:su -
-password1
root@home:/etc/init.d/networking restart

if that dont work then mabe your main kernel is messed and only your recovery one works right......

:popcorn:

---

