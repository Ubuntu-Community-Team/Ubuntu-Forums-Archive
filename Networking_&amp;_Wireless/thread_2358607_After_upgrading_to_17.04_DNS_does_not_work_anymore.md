---
title: "After upgrading to 17.04 DNS does not work anymore"
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by alfas2 on 2017-04-15
I upgraded from 16.10 to 17.04 and DNS does not work anymore. Please help. I tried several suggestions that I found on internet, like:
restarting, reconfiguring resolvconf
disabling  systemd-resolved
removing dnsmasq
Nothing helps. Please help. Maybe there is a way to get back any old working version of dns?

---

### Post by howefield on 2017-04-15
Moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by yesion on 2017-04-16
I have got the same problem :( Any solution halps :(

---

### Post by yesion on 2017-04-16
I have found solution in this post on forum [https://ubuntuforums.org/showthread.php?t=2358660](https://ubuntuforums.org/showthread.php?t=2358660)

My problem is SOLVED
[COLOR=#000000]Code:
sudo gedit /etc/resolvconf/resolv.conf.d/tail[/COLOR]
[COLOR=#000000]Add the following:[/COLOR]

[COLOR=#000000]Code:
nameserver 8.8.8.8[/COLOR]
than RESTART computer

---

### Post by alfas2 on 2017-04-17
Method 2 worked for me. Still I think just to be safe it is better to remove systemd-resolved as if I understand correctly it is causing problems.

---

