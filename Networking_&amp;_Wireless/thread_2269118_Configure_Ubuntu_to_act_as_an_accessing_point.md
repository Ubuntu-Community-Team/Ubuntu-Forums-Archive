---
title: "Configure Ubuntu to act as an accessing point"
date: 2015-03-13
forum: Networking &amp; Wireless
---

### Post by XiaozhouJIA on 2015-03-13
I'm now in my testbed setup and got stuck on configuring the Ubuntu machine as an accessing point.

I have now two laptops (m1, m2) and one desktop (d1), all of them are running Ubuntu 14.04.
Both m1 and m2 have two interfaces: eth0 and wlan0. d1 has an eth0.

Now I'm connecting m2.eth0 and d1.eth0 on a switch. There is another port on the same switch which connects to the Internet. 
And I'm using m2 as an accessing point, connecting m1.wlan0.

The setup looks like this

[https://www.dropbox.com/s/4tqwmtjca7pe1ue/topo.png?dl=0](https://www.dropbox.com/s/4tqwmtjca7pe1ue/topo.png?dl=0)

Setup other than topology:
1. in /etc/sysctlconf of m2, it reads net.ipv6.conf.all.forwarding=1 
2. configured radvd on m2.wlan0. so m1 get another ipv6 address from m2.wlan0


What happens now:
1. I can ping from m1.wlan0 to m2.wlan0, both IPv4 and IPv6.
2. I can ping from m2.eth0 to d1.eth0, both IPv4 and IPv6.
3. I CAN ping from m1.wlan0 to d1.eth0, in IPv4.
4. I CAN'T ping from m1.wlan0 to d1.eth0 in IPv6. (says Destination unreachable: Address unreachable)

And I want to ping d1.eth0 from m1.wlan0. 

Here is what I have already tried.
1. Configured global ipv6 address for four interfaces involved. Put in an route entry in m2, saying divert traffic looking for d1.eth0 to m2.eth0.
2. I thought it was because routing table in m2 is not configured correctly, so I did a lot dirty work using ip6tables. Can't remember exactly what I did now...



Any comments or hints would be highly appreciated. 
Thanks in advance.

---

