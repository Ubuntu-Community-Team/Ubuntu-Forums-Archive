---
title: "SSH on more then one port"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by Quadcore on 2008-03-05
Can someone point me in the right direction on an example of running openssh on more then one port, I dont mind using more then one sshd init file if needed..

---

### Post by Fire_Chief on 2008-03-05
Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=464981]("http://ubuntuforums.org/showthread.php?t=464981")

---

### Post by HermanAB on 2008-03-05
In file /etc/ssh/sshd_config put:
Port 22
Port 2222
Port 1111
...

Then restart sshd and ensure that these ports are open in your firewall.

Cheers,

Herman

---

