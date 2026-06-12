---
title: "Adviced Netwtork Settings? (/etc/sysctl.conf)"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by asezen on 2008-09-07
Hello guys,

I would like to have some advise and review for these settings for my ubuntu hardy server. I am running a torrent seedbox with 100/100mbit, 1gb ram and 1.2+ Ghz CPU . Which tweaks i should do to my ubuntu server ? Your advices will be appreciated.

Thanks

###/etc/sysctl.conf
##
# some of the defaults may be different for your kernel call this file with
# sysctl -p  these are just suggested values that worked well to
# increase throughput in several network benchmark tests,

### IPV4 specific settings
# turns TCP timestamp support off, default 1, reduces CPU use
net.ipv4.tcp_timestamps = 0
# turn SACK support on -- you probably want this off for 10GigE
net.ipv4.tcp_sack = 1
# scalling support
net.ipv4.tcp_window_scaling=1
# on systems with a VERY fast bus to memory interface this is the big plus
# sets min/default/max TCP read buffer, default 4096 87380 174760
# setting to 100M - 10M is too small for cross country (chsmall)
net.ipv4.tcp_rmem = 1000000 1000000 1000000
# sets min/pressure/max TCP write buffer, default 4096 16384 131072
net.ipv4.tcp_wmem = 1000000 1000000 1000000
# sets min/pressure/max TCP buffer space, default 31744 32256 32768
net.ipv4.tcp_mem = 150000000 150000000 150000000

### CORE settings (for socket and UDP effect)
# maximum receive socket buffer size, default 131071
net.core.rmem_max = 1000000
# maximum send socket buffer size, default 131071
net.core.wmem_max = 1000000
# default receive socket buffer size, default 65535
net.core.rmem_default = 2524287
# default send socket buffer size, default 65535
net.core.wmem_default = 2524287
# maximum amount of option memory buffers, default 10240
net.core.optmem_max = 2524287
# number of unprocessed input packets before kernel starts dropping them, default 300
net.core.netdev_max_backlog = 300000
# enable window scaling RFC1323 TCP window scaling
net.ipv4.tcp_window_scaling=1

---

### Post by asezen on 2008-09-08
No idea ?

---

