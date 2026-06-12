---
title: "Manual IP Table edits reverted after few minutes"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by mlapaglia on 2008-10-31
I have IP route automatically set up by Ubuntu when the computer is turned on. Afterwards I have a script that enables basic round-robbin abilities that turns:

```

192.168.2.0/24 dev eth1  scope link  src 192.168.2.5 
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.5  metric 1 
192.168.1.0/24 dev eth0  scope link  src 192.168.1.2 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
xx.93.xx.0/23 dev wlan0  proto kernel  scope link  src xx.93.xx.127  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 

```

to this:

```

mlapaglia@jennifer-desktop:~$ ip ro
192.168.2.0/24 dev eth1  scope link  src 192.168.2.5 
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.5  metric 1 
192.168.1.0/24 dev eth0  scope link  src 192.168.1.2 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
xx.93.xx.0/23 dev wlan0  scope link  src xx.93.xx.xx 
xx.93.xx.0/23 dev wlan0  proto kernel  scope link  src xx.93.xx.127  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default 
	nexthop via 192.168.1.1  dev eth0 weight 1
	nexthop via 192.168.2.1  dev eth1 weight 1
	nexthop via 64.93.222.1  dev wlan0 weight 1

```

Is there a way to allow Ubuntu to initally set up my IP tables, but then not alter them afterwards?

---

### Post by mlapaglia on 2008-11-01
bueller? I've tried some guides from google but nothing sticks, network-manager keeps messing with my settings :(.

If i disable it on startup, it doesn't create the inital network, and I've had a hard time doing it myself..

---

### Post by mlapaglia on 2008-11-02
After a day of trying I figured it out, here's a guide I wrote:
[https://help.ubuntu.com/community/IProuteRoundRobbin](https://help.ubuntu.com/community/IProuteRoundRobbin)

---

