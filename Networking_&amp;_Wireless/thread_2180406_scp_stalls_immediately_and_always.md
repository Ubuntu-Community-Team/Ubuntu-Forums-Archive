---
title: "scp stalls immediately and always"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by hubert-johannsen on 2013-10-12
I have a strange problem transfering file. Whatever the size of the file, whatever the moment, scp transfer immediately stalls.
I have opened port 22 between the two machines, and the communication opens, but visibly some packets are lost, and the protocol gets nuts.
I also have an openvpn connection between the machines, and over that connectino, the scp transfer passes immediately. 
Anyone have observed a similar behavior? 
thanks and greetings,
Hubert

---

### Post by jacobsallan on 2014-03-08
Try entering 'sudo sysctl -w net.ipv4.tcp_sack=0' in a terminal before attempting the scp.  The setting will be lost after the next shutdown or reboot.  If you can stomach the loss of performance, add a line to  /etc/sysctl.conf: 'net.ipv4.tcp_sack=0' .

[http://superuser.com/questions/593735/tcp-header-option-sack-permitted-selective-acknowledgments-negotiation](http://superuser.com/questions/593735/tcp-header-option-sack-permitted-selective-acknowledgments-negotiation) and [http://serverfault.com/questions/10955/when-to-turn-tcp-sack-off](http://serverfault.com/questions/10955/when-to-turn-tcp-sack-off) are two references on the topic.

There is network gear out there that do not implement this protocol or implement it incorrectly.  Basically, if a packet is dropped or forced out of sequence by a firewall, your site's network equipment does not support SACK, and your local machine's network driver does implement TCP/SACK then the parties will not recover the same way.  The result will be a swarm of retransmitted packets that your scp session will not recover from.

---

