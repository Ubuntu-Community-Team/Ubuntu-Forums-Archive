---
title: "DNS problem"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by aaronsharpe on 2008-01-26
Ubuntu is detecting my main DNS server as 192.168.2.1 (my router) and then putting the other DNS servers (the ones actually provided by my ISP) underneath that.

Using 192.168.2.1 as the DNS server doesn't work and so I have to wait for it to time out and try another DNS server before a website will load.

Deleting it from the network management thing fixes the problem but I have to go back and do it every time I reconnect to me router.

So is there any way I can make it delete it automatically?

I have the same problem on both my laptop and desktop.

---

### Post by Iowan on 2008-01-26
Are you using DHCP?  If so, check **/etc/dhcp3/client.conf** file. It may help to get rid of the **domain-name-servers** part of the REQUEST line. (Make a backup of the file first - in case of bad advice...)

---

### Post by kevdog on 2008-01-26
Here is an example of how you might configure your setup:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

