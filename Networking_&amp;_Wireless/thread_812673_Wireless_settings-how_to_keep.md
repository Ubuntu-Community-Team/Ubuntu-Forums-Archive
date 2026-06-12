---
title: "Wireless settings-how to keep?"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by Milardo on 2008-05-30
Hi, I got my internet working by following this doc 

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

and able to get on internet through nmapplet, not by network manager manual config. Anyways, where can I make a profile or save internet ssid/encryption/password so I can just click on it and get on the internet and not have to reenter settings everytime.

---

### Post by elamericano on 2008-05-30
Network Manager remembers the configuration and password for networks that you have connected to. When you disconnect ethernet it will go into search mode, and it should find your wireless network and connect by itself. After a couple minutes, if it doesn't find your network it will stop searching to save battery. If you click nmapplet and select the network you want, again it will connect. You will not be prompted to re-enter your credentials.

Is it not working like this for you?

---

### Post by Milardo on 2008-05-30
Well, my router isn't broadcasting its ssid.

---

### Post by linuxology on 2008-05-30
When you reboot your settings go away?

---

### Post by Milardo on 2008-05-30
No it is kept in the edit wireless network settings, but how do use that to connect to non broadcasting ssid?

---

