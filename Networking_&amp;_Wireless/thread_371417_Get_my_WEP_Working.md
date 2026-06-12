---
title: "Get my WEP Working"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by Loki1989 on 2007-02-26
I go the ultimate edition and it is working beautifully. Installed my Wireless nicely and quickly an dit has beryl... no Ati drivers yet. I need To get my WEP working first so I can Update it all. I also require the ability to not have to be online for this because I cant directly hook up.

---

### Post by chili555 on 2007-02-27
Get the WEP key from your router and check it twice. We do not want the passphrase, we want the alphanumeric key, something like this: 93c8530b2df51711bad5596f91.

Then, sudo gedit  /etc/network/interfaces to make the relevant interface entry look like this:
```
auto wlan0
iface wlan0 inet dhcp
wireless-key 93c8530b2df51711bad5596f91 
``` Your interface may be eth1, ath0 or ra0, etc.

Check your work twice. Then restart networking sudo /etc/init.d/networking restart and you should be all good.

---

### Post by Loki1989 on 2007-02-27
thanks that helped so much you have no Idea so I am on now and will post more when needed.

---

### Post by lsutiger on 2007-03-02
Thanx a bunch! That worked great! I have been fighting this problem since yesterday.
Appreciate the help!

---

### Post by lsutiger on 2007-03-02
Ok - it owrked...sorta. Everytime I reboot I have to enter the restart command. Why is that and how can I alleviate this problem?

---

### Post by FIONEX on 2007-03-02
Follow these instructions, but when you get to the end DONT RESTART, just do the "/init.rc/dbus restart" command. After you do that, run "nm-applet" and you're all good.
[http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)

---

### Post by lsutiger on 2007-03-02
Broken Link

---

### Post by spd106 on 2007-03-04
I think this [link](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) will work

---

