---
title: "Suddenly lost my network connection"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by donutt on 2007-03-05
My Dapper Drake installation suddenly stops connecting to my Linksys cable modem router and thus I can't connect to the internet anymore.  The installation was set up last year April and I've never had any networking problems until this morning.  I can't even ping my own router 192.168.1.1(it says the network is unreachable).  I tried /etc/init.d/networking restart and it says:

DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable

I've tried rebooting both the machine and the Linksys and the problem is still there.  The router is working fine becase my WindowsXP hooked up to the same Linksys works.  It's not the cable coze I've tried switch cables with the WindowsXP machine.  I don't remember installing any software recently.  The last thing I did was last night when I transferred file from this ubuntu machine to a a laptop running Edgy via SSH.

I'm not very familiar with Linux.  Can any kind souls help me debug/fix this?  
Thanks.

---

### Post by Mr. C. on 2007-03-05
Please show some Ethernet info.  This first post is a good example of what you should post:

[http://www.ubuntuforums.org/showthread.php?t=377009](http://www.ubuntuforums.org/showthread.php?t=377009)

MrC

---

