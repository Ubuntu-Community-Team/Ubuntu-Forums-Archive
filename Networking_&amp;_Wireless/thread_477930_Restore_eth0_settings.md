---
title: "Restore eth0 settings"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by yonib on 2007-06-18
Hi,
I'm using 2.6.17 kernel.

My ether card is: Realtek RTL8139/810x Family Fast Ethernet NIC 

Trying to solve the problem described in my previous post (ubuntu connection stalles when trying to upload to siteground, while the same machine/DSL using WinXP succeeds...) - I ruined my eth0 settings. now my ubuntu cannot do TCP (firefox, FTP, mail... fails to connect), aMule connects OK.

When sniffing (wireshark) the connection it shows that the data actually goes back and forth from firefox to the outer world, but somehow it's not acknowledged and concluded on my side.

Could anyone please help me restore the settings. I did what was suggested in:
[http://dsd.lbl.gov/TCP-tuning/linux.html:](http://dsd.lbl.gov/TCP-tuning/linux.html:)

[COLOR="Red"]>vi /etc/sysctl.conf[/COLOR]
# increase TCP max buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
# increase Linux autotuning TCP buffer limits
# min, default, and max number of bytes to use
net.ipv4.tcp_rmem = 4096 87380 16777216 
net.ipv4.tcp_wmem = 4096 65536 16777216
# don't cache ssthresh from previous connection
 net.ipv4.tcp_no_metrics_save = 1
# recommended to increase this for 1000 BT or higher
 net.core.netdev_max_backlog = 2500
# for 10 GigE, use this
# net.core.netdev_max_backlog = 30000   

[COLOR="red"]> sysctl -p[/COLOR]

[COLOR="red"]>ifconfig eth0 txqueuelen 1000[/COLOR]

and now I'm reduced to using WinXP....

---

