---
title: "networking speed up"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by s9032g@comcast.net on 2015-04-22
Is there a simple way to disable ipv6 in 14.04? All I can find are directions involving a lot of terminal commands. Seems that it should be simple as in unchecking it in Windows.

Often in Ubuntu I have finally found a simple solution after reading a lot of complex ones.

---

### Post by TheFu on 2015-04-23
Sure. Blacklist the ipv6 module in /etc/modprobe.d/blacklist.conf

---

### Post by h-schuett1990 on 2015-04-23
If you use the network manager it is a simple as unchecking it in windows.

simply go to the connection you use in edit connections. In the part about IPv6 settings there is a method field which you can set to 'ignore'. This will turn IPv6 off for this connection.

Only drawback is that you have to repeat it for each connection

---

### Post by s9032g@comcast.net on 2015-04-23
Schuett

Thank you.

See what I mean about simple solutions needing to be searched for, Black listing takes several steps in terminal and is prone to error because of the details. Occam's razor is the answer.

---

### Post by TheFu on 2015-04-23
> **s9032g@comcast.net said:**
> Schuett

Thank you.

See what I mean about simple solutions needing to be searched for, Black listing takes several steps in terminal and is prone to error because of the details. Occam's razor is the answer.

Plus it appears that my answer may not always be correct anymore. I don't know when this changed.
Google found this answer: [https://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04](https://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04)

[https://askubuntu.com/questions/309461/how-to-disable-ipv6-permanently](https://askubuntu.com/questions/309461/how-to-disable-ipv6-permanently) shows a few different methods, should one not work. Some distros are harder than others to stop IPv6.

Anyway, glad you found a method that fits your needs. Be certain to verify that it actually DID disable IPv6, since it may not always work.

---

### Post by s9032g@comcast.net on 2015-05-07
Ipv6 was successfully disabled

---

