---
title: "Very Slow Internet in Ubuntu 8.04"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by NW2190 on 2008-05-10
Hi, I have recently installed Ubuntu 8.04 and after the install I found that my internet connection was quite terrible.  I have a wired connection straight to my router so the threads I've seen on slow internet in Hardy have been pretty much useless (being centered around wireless).  The main problem is that Firefox waits at "Looking up www.example.com..." for a long time, making browsing the internet ridiculously slow.  It also seems to affect downloading from the repos, however, leading me to think it's not a firefox issue.  I've tried changing to OpenDNS and disabling IPv6 with no luck. Does anyone know how to fix this?

---

### Post by SINternet on 2008-05-15
I will post my sysctl.conf and rc.local files tonight for you to try and boost your speed. 

SIN

---

### Post by SINternet on 2008-05-15
I have the dreaded rt2500 card WMP54G. 

After a fresh install I applied these files only and got the Internet Speed out of my system I was used to seeing with Windows.

Paste applicable contents from each file.

My additions to the sysctl.conf

To open for editing "sudo gedit /etc/sysctl.conf"

#increase TCP maximum buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216

# increase linux autotuning TCP buffer limits
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1

# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_timestamps=0
net.ipv4.tcp_moderate_rcvbuf=0
net.ipv4.tcp_window_scaling=0

to apply immediately after editing "sudo sysctl -p"

Good source of info here. [http://www-didc.lbl.gov/TCP-tuning/TCP-tuning.html](http://www-didc.lbl.gov/TCP-tuning/TCP-tuning.html)


Nice Info here.......[http://www.extremetech.com/article2/0,2845,2114124,00.asp](http://www.extremetech.com/article2/0,2845,2114124,00.asp)

Info on sysctl.conf parameters..[http://frankmash.blogspot.com/2005/11/sysctl-kernel-optimization.html](http://frankmash.blogspot.com/2005/11/sysctl-kernel-optimization.html)

check your parameters by dumping the sysctl info to a file.
sudo sysctl -A > ~/Desktop/sysctl_settings

rc.local            has some redundancy to syctl.conf

paste before the exit 0 at the bottom

/sbin/iwconfig wlan0 rate 11M

echo 256960 > /proc/sys/net/core/rmem_default
echo 256960 > /proc/sys/net/core/rmem_max
echo 256960 > /proc/sys/net/core/wmem_default
echo 256960 > /proc/sys/net/core/wmem_max

echo 0 > /proc/sys/net/ipv4/tcp_timestamps 
echo 1 > /proc/sys/net/ipv4/tcp_sack 
echo 1 > /proc/sys/net/ipv4/tcp_window_scaling

"11M" worked fine for my connection. Play with that rate till you find your sweet spot (because not every place has the same basic speed nor does everyone pay for more speed like Business Class)

Most people say make a backup of the original but I say make a backup of your edited file as well!

SIN[COLOR="PaleTurquoise"][/COLOR]

---

### Post by UnRkiSt on 2008-05-16
I'm having the same problem as well on 8.04 (hardy). Ping responses (if any) to known working servers are VERY slow and web browsing crawls with many "server taking too long to respond" messages. top reports may 'gettys' running (5-6), with only one virtual terminal open.  Any help appreciated. TIA.

---

