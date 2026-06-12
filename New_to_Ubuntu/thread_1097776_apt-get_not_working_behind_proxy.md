---
title: "apt-get not working behind proxy"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Akumos on 2009-03-16
Hi, been playing with KDE and can't get apt-get to work. We are behind a firewall and the settings are correct in the Network Settings menu.

/etc/apt/apt.conf doesn't seem to exist.

Do I create it? And put proxy settings in?

Also, in gnome is use nano to edit files, what do I use in KDE? Kate springs errors and gedit isn't installed.

Thanks

---

### Post by albandy on 2009-03-16
the configuration files are inside apt.conf.d
/etc/apt/apt.conf.d

---

### Post by sugi007 on 2009-03-16
to temporarily get apt-get working behind a proxy you can do the following

in a terminal type the following

sudo export http_proxy=http://[user:password@]proxy:port

[user:password@] is only required if you need authentication for your proxy

you need sudo if apt-get needs sudo

---

