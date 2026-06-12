---
title: "Easy access to my IP address"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-14
I frequently need to copy/paste my ip address as I have dynamic IP. Currently I follow the tedious process on right-clicking my net connection, click connection information and getting my ip from there. Is there an easier and faster way to access it? Like have it on my taskbar or desktop or any other method?

---

### Post by HarrisonNapper on 2009-12-14
ifconfig for internal ip, [www.whatismyip.com](www.whatismyip.com) for external ip

Cheers.

---

### Post by kellemes on 2009-12-14
You can use [Conky]("http://conky.sourceforge.net/") to put it on your desktop.
[This thread]("http://ubuntuforums.org/showthread.php?t=868156") explains how to get ip shown by Conky.

---

### Post by theozzlives on 2009-12-14
Put a launcher to terminal on the panel, from terminal type:
```
ifconfig
```

---

### Post by kellemes on 2009-12-14
[Giplet]("http://giplet.sourceforge.net/")
```
sudo apt-get install giplet
```
and add it to the Gnome Panel.

---

### Post by rkakkar on 2009-12-15
thanks!

---

