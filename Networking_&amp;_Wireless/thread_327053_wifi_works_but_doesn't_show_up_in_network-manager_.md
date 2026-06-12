---
title: "wifi works but doesn't show up in network-manager (nm-applet)"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by strabes on 2006-12-28
Yes well the title pretty much explains my problem. Currently I am connected through System -> Administration -> Networking. 

I am currently at home and need network-manager to be able to scan for wireless networks for when I am back at school in Chicago. Is there a command for network manager to fix my problem? If you need more information just tell me what to type into a terminal. Thanks.

---

### Post by Dr0n3 on 2006-12-29
I had the same thing. I did some searching and found this.
[http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6)

It solved the problem. Appearantly Network Manager doesn't use interfaces if they're being managed by Gnome Networking in System > Administration > Networking. It stores the status and configuration of interfaces in /etc/network/interfaces.

So all you have to do is sudo gedit /etc/network/interfaces and comment out the interfaces you want Network Manager to manage. That's it! ;)
Don't forget to reboot, or restart networking.

---

### Post by strabes on 2006-12-29
thanks! that worked perfectly.

---

