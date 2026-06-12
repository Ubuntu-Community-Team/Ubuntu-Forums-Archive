---
title: "Increase Your Internet Connection Speed"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by aspiannur41 on 2011-03-07
I hope it's NO REPOST


> sudo gedit /etc/sysctl.conf
and next add this at end of line 

> # increase TCP max buffer size setable using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
# increase Linux autotuning TCP buffer limits
# min, default, and max number of bytes to use
# set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
# for 10 GigE, use this, uncomment below
# net.core.netdev_max_backlog = 30000
# Turn off timestamps if you're on a gigabit or very busy network
# Having it off is one less thing the IP stack needs to work on
#net.ipv4.tcp_timestamps = 0
# disable tcp selective acknowledgements.
net.ipv4.tcp_sack = 0
#enable window scaling
net.ipv4.tcp_window_scaling = 1


save it and close and write this on terminal
>  sudo sysctl -p


[http://ubuntu-indonesia.com](http://ubuntu-indonesia.com)

---

