---
title: "Net problems with Kernel 2.6.20-15"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Tbay on 2007-04-25
After upgrading to Feisty, and updating the kernel from 2.6.17-10 to 2.6.20-15. I can't receive imap mails and some internet pages does not load in firefox. After booting 2.6.17-10 again it all works fine. does anyone know if there is a bug report on this can't find one.

---

### Post by sdide on 2007-04-25
What does 

~# cat /etc/resolv.conf 

output with the two different kernels loaded?

---

### Post by anu815 on 2007-04-25
This might help!  I was having similar problems and found this article on performance tuning;

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

sudo gedit /etc/sysctl.conf

* Then again, scroll to the bottom and just add these lines to it. 

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

* You have to reset your sysctl for these to take effect. 

sudo sysctl -p

---

### Post by maxol on 2007-04-25
Same problem [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=419844").

I've tried anu815's tweak but it didn't work for me.

---

