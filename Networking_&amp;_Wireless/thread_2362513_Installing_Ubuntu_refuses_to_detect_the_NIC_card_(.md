---
title: "Installing Ubuntu refuses to detect the NIC card (unable to Connect to Wifi)"
date: 2017-05-29
forum: Networking &amp; Wireless
---

### Post by harnando98 on 2017-05-29
Now I've installed 2 different versions of Ubuntu onto my inspiron 3520 laptop and neither one is able to connect to the internet wirelessly, unlike when I have windows 10 installed can recognize wireless NIC on the damn thing. I don't know whats going on and I'm new to linux os so, if any help can be said, I'd appriciate it thanks.

---

### Post by Frogs Hair on 2017-05-29
Moved to* Networking & Wireless *

---

### Post by Hadaka on 2017-05-29
Hi, from a working wired connection please Copy and paste
one line at a time..
```
sudo apt-get update
```
then do and post the output of...
```
rfkill list all
uname -a | awk '{print $3,$12}'
lspci -n | awk '/0280|0200/{print$3}'
```
Thanks.

---

