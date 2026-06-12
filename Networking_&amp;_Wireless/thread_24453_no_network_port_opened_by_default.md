---
title: "no network port opened by default ?"
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by kixvn on 2005-04-07
when I did "nmap localhost" on a fresh hoary install (which i removed some packages), it said that *no network port is opened"
how do I open some important ports ?
thks

---

### Post by dataw0lf on 2005-04-07
1) Ensure that your hosts.allow and hosts.deny files are allowing connections

2)  Install some servers.  Read the documentation.  OpenSSH and Apache are some good starting points.  

3) If you have a router/DSL modem, ensure that the ports you want accessible from the internet are forwarded to the server.

Remember: Google is your friend.

---

### Post by kixvn on 2005-04-07
I did search google but couldn't find some solution
I did install apache + mysql + php , but also can't access [http://localhost](http://localhost) from my browser
nmap localhost show this
```

WARNING:  Could not determine what interface to route packets through to 127.0.0.1, changing ping scantype to ICMP ping only
pcap_open_live: ioctl: No such device
There are several possible reasons for this, depending on your operating system:LINUX: If you are getting Socket type not supported, try modprobe af_packet or recompile your kernel with SOCK_PACKET enabled.
*BSD:  If you are getting device not configured, you need to recompile your kernel with Berkeley Packet Filter support.  If you are getting No such file or directory, try creating the device (eg cd /dev; MAKEDEV <device>; or use mknod).
SOLARIS:  If you are trying to scan localhost and getting '/dev/lo0: No such file or directory', complain to Sun.  I don't think Solaris can support advanced localhost scans.  You can probably use "-P0 -sT localhost" though.

```

also i can't use "telnet localhost" which I can do by defaut on every other distro i tried

any ideas how to solve this ?

---

### Post by dataw0lf on 2005-04-07
You have no route to your localhost.  First, give me your ifconfig output (lo is down, but I'd like to see it).  Then try:
ifup lo

if that doesn't work try:

ifconfig lo 127.0.0.1

if that doesn't work try:

route add -net 127.0.0.1 lo

if none of these work, dump your /etc/network/interfaces here

---

