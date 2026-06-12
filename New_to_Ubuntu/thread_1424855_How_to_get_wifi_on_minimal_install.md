---
title: "How to get wifi on minimal install?"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by pall111 on 2010-03-08
edit: Problem solved! :]

Hello, having gotten fed up with ubuntus bloat i decided to do a minimal install using xfce as the desktop manager as i have had good experience with xubuntu. Now i am at a loss as how to get wifi like in xubuntu, what do i need to install to get wifi?

I currently have wireless-tools installed... 

Thanks :]

---

### Post by koleoptero on 2010-03-08
The xubuntu and ubuntu installs are using network manager applet. To get that:

sudo aptitude install nm-applet

It might pull in a lot of dependencies to work though, you'll have to see that for yourself. If you want to use something lighter you'll have to use wicd, but unfortunately I don't know how it works. A search on it is sure to help you though.

---

### Post by undecim on 2010-03-08
The network-manager-gnome package has the network manager that comes with Ubuntu and Xubuntu

There is also Wicd, which is my personal favorite network manager.

If you don't want those, you will have to learn to use wpa_supplicant to connect with a terminal: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136). You could, of course, create your own scripts if you want.

---

### Post by pall111 on 2010-03-08
Thanks guys i install wicd and it works perfect. :P

---

