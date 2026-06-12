---
title: "Freeciv 2.1.5 - Connection refused"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Xarver on 2009-02-01
Hello, I try to connect to my brother's freeciv game locally although it says connection refused whenever I try to. 
We are both using ubuntu 8.10 and freeciv 2.1.5

The only thing it says when I try to connect to host ubuntu port 5556 is
"Connection Refused."
How can I connect to his freeciv game?

Any help appreciated! :)

---

### Post by ibuclaw on 2009-02-01
If you are behind a router, it may be that you need to **port forward** your brothers (or your own) local IP address so that you can connect to it.
To do this, you login to your router through firefox by typing in
```
192.168.1.1
```(username and password required) and configure it.
If you are unsure of who has which IP address, use:
```
ifconfig | grep inet
```
to ascertain it.

Also, ensure that the firewall is not enabled, or if it is, make an exception on port 5556 on the computer that is hosting the game.
```
sudo ufw status
```
If the above returns the answer **Firewall loaded**, then run the following:
```
sudo ufw allow 5556
```
and hopefully that should point you in the right direction to resolving your problem :)

Regards
Iain

---

