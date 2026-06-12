---
title: "tcp gurus: tcp window scaling"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by corwinspyre on 2007-04-04
I recently reinstalled Ubuntu (feisty fawn 64bit) and had very slow internet connections.  Turning off ipv6 didn't help, but setting ```
echo "4096 16384 131072" > /proc/sys/net/ipv4/tcp_wmem
echo "4096 87380 174760" > /proc/sys/net/ipv4/tcp_rmem
``` as described _[here](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)_ made it reasonable.  I now can get around 200-300kb/sec downloads (which is still low--i'm on a small campus with a 60mb/sec download connection), but it drops to 4000 to 8000 bytes/sec every 10 seconds or so maybe, so I'm assuming I have to change the values to something else.  How do I figure out what values I should be using?  Thanks a lot!


Edit: here is the solution that worked for me in the hope that it helps someone else (or is that a bad thing? :P)
In console, ```
sudo nano /etc/sysctl
```
Edit the file to say:
```
# the following stops low-level messages on console
kernel.printk = 4 4 1 7
#VIA http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

#VIA http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed
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
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
```Basically, it's straight from the wiki at tvease.net (link in quote above), except instead of the lines net.ipv4.tcp_wmem = 4096 87380 524288, net.ipv4.tcp_rmem = 4096 87380 524288, I have net.ipv4.tcp_wmem = 4096 16384 131072 and net.ipv4.tcp_rmem = 4096 87380 174760 via an inodes.org blog (it's in the original post and also in the quote)

---

