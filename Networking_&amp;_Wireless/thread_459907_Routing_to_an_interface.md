---
title: "Routing to an interface"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by MasonS on 2007-05-31
Hi, I'll give a quick explanation of what I want to do and what I already have setup:

I have two wireless NICs installed on this PC.
wlan0 is used for virtual machines.
ath0 is used for the internet for music/video/downloads
My virtual machines are currently using wlan0 without any issues.
I don't know if Ubuntu is using wlan0 or ath0 by default.

Can I route requests by 192.168.1.x to ath0? Or, is there a simpler way? Thanks in advance.

```
auto wlan0
iface wlan0 inet static
address 10.0.0.20
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1
dns-nameservers 10.0.0.1
wireless-essid wireless1

auto ath0
iface ath0 inet static
address 192.168.1.20
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
wireless-essid wireless2
```

p.s: By dropping the interfaces with ifup/down I was able to confirm that both interfaces work

---

### Post by jonallport on 2007-05-31
Hi  MansonS,

Really simple, you just need to give the prefered interface a lower metric for routing.

In your example, add the line 'metric 20' to the wlan0 entry and 'metric 10' to ath0.

This will give ath0 a higher priority in the kernel routing table (as seen if you type 'sudo route')

Hope that answers your question.
J

---

### Post by MasonS on 2007-06-02
I added the metric line to my etc/network/interfaces but I don't think it's working.
Whenever I max out wlan0 with file transfers in my virtual machines I can't surf at all in Ubuntu.

```
auto wlan0
iface wlan0 inet static
address 10.0.0.20
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1
dns-nameservers 10.0.0.1
wireless-essid wireless1
metric 20

auto ath0
iface ath0 inet static
address 192.168.1.20
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
wireless-essid wireless2
metric 10
```

This is what it looks like when I sudo route

```
nitz@nitz-laptop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     0      0        0 ath0
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
default         10.0.0.1        0.0.0.0         UG    20     0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 eth0
```

---

### Post by jonallport on 2007-06-04
I think it's going to have to be a more somplex solution.  By brain hurts right now, so I'll have a think later.

Just to summarise, you want Ubuntu to use ath0 ONLY and your VMs to use wlan0 ONLY?

OK, let me think...what VM software are you running?

J

---

