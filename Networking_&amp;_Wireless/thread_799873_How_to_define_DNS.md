---
title: "How to define DNS?"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by alex sun on 2008-05-19
Dear inhabitants of the forum,
I kindly ask you to help me with 1 little problem:
I installed hardy 64.
Every time when I use DHCP wlan0, my DNS for eth0 disappears and I have to define it again. How to define DNS once and forever?

---

### Post by superprash2003 on 2008-05-19
read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by alex sun on 2008-05-21
2 superprash2003.
Thanks anyway.
I tried it, but seems that your suggestion doesn't work for me.
My home Internet provider has 2 specific DNS addresses that must be defined in my connection settings. Otherwise the Internet will not work. Also I have constant IP and I use eth0 connection at home.
At university my IP is defined by DHCP and I use wlan0. When connect to a university wireless network, my DNS addresses defined in connection settings disappear and I have to redefine then when I return to home.
It's just a bit annoying..
Could anyone help with this problem, please?

---

### Post by helgman on 2008-05-21
I just researched this a little while back and found three suggestions on how to fix it. The first one is not an open in your case. The second one looks a loot like the one linked to above with the exception that you should reboot your system or bring down/up the interfaces. The third one involves changing the permissions on the file.

You'll find them here: [http://ubuntuforums.org/showpost.php?p=4977675&postcount=5](http://ubuntuforums.org/showpost.php?p=4977675&postcount=5)

Regards,
Helgman

---

### Post by alex sun on 2008-05-23
Thanks a lot, helgman!
It really works! :-)

---

