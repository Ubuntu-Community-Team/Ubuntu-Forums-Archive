---
title: "HP Pavilion 15 notebook pc"
date: 2020-04-09
forum: Networking &amp; Wireless
---

### Post by gerryinmkg on 2020-04-09
Hi all, I'm new to linux and ubuntu 18.04. I've read multiple articles on getting my wired connection to work and have run several in the terminal but not having much luck. My wireless works fine but
can't seem to get the wired connection button turned on. The cable is fine and it works with my other laptop running windows 10 and also my desktop with windows 10. It seems as though the
realtek cards have problems but would like to strictly use a wired connection. I'll try and put in the scripts of my machine to give an idea on what I have. I'm not used to using a terminal but at 68 yrs old I can still try and learn something new. Thanks in advance for all your help.):P

---

### Post by pcfan1234 on 2020-04-10
Please type 

```

lsb_release -a
lspci -nnk
sudo apt install ethtool
ip a

```
in the Terminal and post the output here in the forum, please don't use LibreOffice, this takes very long to load on my old Dell D600.

---

### Post by gerryinmkg on 2020-04-10
I'll give it a shot. Thanks I sure hope this works.

---

### Post by gerryinmkg on 2020-04-11
Maybe I should try another distro. I've used manjaro and zorin and linux mint. Everything I seem to try doesn't do any good. I've tried to work in the nano and get nothing.:confused:

---

