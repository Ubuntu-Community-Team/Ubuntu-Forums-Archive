---
title: "Fixed internet connection 8.04"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by coolclassic on 2008-05-02
Fixing my internet connection :lolflag: involved two processes:

1)8.04 is installed with roaming access only.Use system/network to edit settings manually for dhcp.

2)apparently window scaling is still a problem the following file needs to be edited- sysctl.config you'll find it in etc. Once open cut and paste the follwing:

#-----------------------------------------------------
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

# [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)
vm.swappiness=0
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

#---------------------------------------------------------------
Once saved using termanal do  su sysctl -p 
network should now be working

The above info may not all be needed but someone more knowledgeable may give another suggestion

---

