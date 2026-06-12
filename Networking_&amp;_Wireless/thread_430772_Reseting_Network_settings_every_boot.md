---
title: "Reseting Network settings every boot"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by daviderukh on 2007-05-02
I've just installed the new addition of kubuntu 7.04
I have a problem that all Network settings is reset when I restart the compuer.
each time I have to change the DNS, erase the default gateway (should me blank but set to 0.0.0.0) and resent  eth0 so it'll obtain its ip adress. Only then the Internet connects

I read this post [http://ubuntuforums.org/showthread.php?t=6704](http://ubuntuforums.org/showthread.php?t=6704) but it didn't help because the file  /etc/dhcp3/dhclient-script doesn'e exits.

Can anyone help me?

---

### Post by Floppyjoe on 2007-05-02
This link may be of help to you.
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by daviderukh on 2007-05-02
Didn't help. :(
So I added the line 
 supersede domain-name-servers 212.150.49.10, 62.90.133.233;
to the file /etc/dhcp3/dhclient.conf and rebooted the computer.
DNS was saved all right, but Internet didn't work - dispite of all my attempts to do what I previetly done.
So I removed this line, rebooted, chanded DNS and other settings manually  and hear I am online.

Any Ideas what shoul I do next?
Thank you
David

---

### Post by daviderukh on 2007-05-03
Anybody can help me pls?

---

