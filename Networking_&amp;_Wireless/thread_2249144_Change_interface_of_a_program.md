---
title: "Change interface of a program"
date: 2014-10-19
forum: Networking &amp; Wireless
---

### Post by avaerf on 2014-10-19
Hi, i'm have 2 interfaces in my computer, and i'm tring change the primary interface of a program, example, use eth0 in chrome and wlan0 in wget, i don't know how to do this thx.

---

### Post by TheFu on 2014-10-19
If I understand the question ... 

Networking is system-wide, not per program.

You could setup dual networking to specific network subnets using manually configured routing tables - this is NOT per program.
Or you could enable wifi and use wget **then** disable wifi and enable eth? and use any other program you desire.

There might be a way to accomplish this through different userids and SELinux by limiting access to the devices by cgroup (I dunno), but that is beyond my skills. Sorry.

For servers (software with network listeners), many, like apache or ssh, have specific settings inside the config file for which interface (i.e. network device) to listen on.  This only works for inbound connections, not outbound.

Hope this helps.  If I misunderstand, please correct as needed.

---

### Post by davit2 on 2014-10-20
Hi, 
use different users for different programs(for example run chrome us your current username(without sudo) and wget us a root(with sudo)).

and do this

sudo iptables -t nat -I OUTPUT -m owner --uid-owner root -j DNAT --to-destination 192.168.1.1  <-----  (change this IP with your wlan0 IP address)
sudo iptables -t nat -I OUTPUT -m owner --uid-owner "current_user_name" -j DNAT  --to-destination 192.168.2.1  <-----  (change this IP with your eth0  IP address, and current_user_name with your username)

after it, if you run programs with sudo, they will use wlan0, and programs without sudo will use eth0.

---

### Post by avaerf on 2014-10-20
Thx davit2, with that my problem is solved,

---

### Post by TheFu on 2014-10-20
Does one of the userids need to be root/sudo?

---

