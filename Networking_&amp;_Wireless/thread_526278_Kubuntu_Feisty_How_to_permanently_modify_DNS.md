---
title: "Kubuntu Feisty: How to permanently modify DNS?"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by mibadt on 2007-08-15
Hi,
Due to ISP switch, my DNS IPs have changed. While I can modify the DNS via the graphic interface (System setting-->Network setting), these new configuration is LOST once I reboot. How can I change these permanently?


Thanks in advance !  :)

Michael Badt

---

### Post by Steve1961 on 2007-08-15
Edit /etc/resolv.conf

---

### Post by mibadt on 2007-08-15
Steve,
Thanks, but I've tried it without success (resolv.conf get re-written during boot).

---

### Post by Steve1961 on 2007-08-15
Here you go then.  You could also use opendns in the process - it's much faster:

[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

---

### Post by mibadt on 2007-08-16
Thanks Steve!
That provided me with the pointer I was looking for.
Editing /etc/dhcp3/dhclient.conf  solved it!

---

