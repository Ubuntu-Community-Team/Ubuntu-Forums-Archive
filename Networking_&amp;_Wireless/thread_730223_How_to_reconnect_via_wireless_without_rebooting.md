---
title: "How to reconnect via wireless without rebooting"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-03-20
I would like to know the commands to stop and reset my wireless connection. Here is why:

We have construction in our area, and I believe their wireless communication is affecting our wireless router. Whatever the reason, I lose my wireless connection and cannot reconnect. I have tried sudo /etc/init.d/networking restart, but it seems only a reboot works. Is there anything else I can try other than rebooting?

This is a Thinkpad T61p with built-in wireless, which is Intel based.

Edit:
-----------------------------------
I have looked over some of the other similar posts, but they did not seem to address this problem directly.

---

### Post by Netsurfer on 2008-03-21
You can try:
$ sudo /etc/init.d/networking restart

Bye

---

### Post by dm6257 on 2008-03-23
I saw your recommendation to use /etc/init.d/networking restart.  On my laptop the wireless connection uses the eth1 connector.  When I try:
sudo  /etc/init.d/networking restart

 it seems to restart eth0.  Same with force-reload.

Is there a way to point these commands at eth1?

Sorry to butt in to the thread.

Thanks,
DM6257

---

### Post by mrsudo on 2008-03-23
$ sudo ifconfig <interface> down
$ sudo dhclient -r <interface>
$ sudo ifconfig <interface> up

making sure to replace <interface> with your correct one.  mine is wlan0.

---

### Post by cmnorton on 2008-03-24
I had tried restarting networking without success, and will try this at my next opportunity.

---

