---
title: "No Wireless Connection"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by cbniles on 2005-08-03
Ooops.  Nevermind, figured it out.

---

### Post by olive73 on 2005-08-04
root@ubuntu:/home/olive # sudo ndiswrapper -i foobar.inf
ls: /etc/ndiswrapper: No such file or directory
Installing foobar
cp: cannot stat `foobar.inf': No such file or directory
root@ubuntu:/home/olive # ls
Desktop
root@ubuntu:/home/olive # ls /etc/ndiswrapper
foobar
root@ubuntu:/home/olive # ls /etc/ndiswrapper/foobar
root@ubuntu:/home/olive # sudo ndiswrapper -i foobar.inf
foobar is already installed. Use -e to remove it
root@ubuntu:/home/olive # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
root@ubuntu:/home/olive # ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@ubuntu:/home/olive #

---

