---
title: "no wired connection"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by gasior.tt on 2015-02-23
Hi, I haven't found similiar thread so I did new one.

 I've installed ubuntu 14.04 on fresh PC buid. Don't have access to wirless nor wired connection. (I have installed ubuntu without internet connection)
Hardware: 
Asus PCE-AC66 Wireless Adapter
Asus Rampage extreme V(2014) motherboard
               

lspci -nn -d 14e4:
[IMG]http://s21.postimg.org/ok2pwi9uf/image.png[/IMG]

lspci -n | egrep '0200|0280' | awk '{print$3}'
[IMG]http://s27.postimg.org/p9a2lm9z7/image.png[/IMG]

lsmod | egrep 'b43|wl'
rfkill list | grep -i yes
**no output**


I am quite new to ubuntu. Thank you for any help

---

### Post by Hadaka on 2015-02-23
Here ya go...... no internet required Dr Chili special.
[http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)

---

### Post by gasior.tt on 2015-02-23
thanks, it worked!!

---

### Post by mörgæs on 2015-02-23
Good, please mark the thread 'solved'.

---

