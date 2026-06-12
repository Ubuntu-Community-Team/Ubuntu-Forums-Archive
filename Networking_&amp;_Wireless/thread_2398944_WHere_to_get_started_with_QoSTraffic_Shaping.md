---
title: "WHere to get started with QoS/Traffic Shaping"
date: 2018-08-19
forum: Networking &amp; Wireless
---

### Post by jonathanese on 2018-08-19
Quick Summary of setup
Ubuntu 18.04 Server: Router, DNS, DHCP
WebMin: Routing (IPTables), NIC setup
PiHole: DNS, DHCP

OK, so I get phenomenal bandwidth through this setup. I used to struggle to get 80Mbps on my 100Mb connection with my AC-68U, but now I get 120Mbps consistently.

However, since I don't have any QoS or traffic shaping, the bufferbloat is horrendous. I used to use fq_codel and usually got less than 20ms of bufferbloat. Now it consistantly hangs out around 800ms.

But finding out about this stuff has been hard. Obviously harder than a simple off-the-shelf router, but I'm surprised at how little information I can find about it.

1. Does Ubuntu Server already have QoS/Shaping capability built in?
2. If not, what applications would you recommend to add these features?
3. How likely is it to conflict with my current configuration?

Thanks

---

### Post by dave-taht on 2018-08-19
the sqm-scripts make configuriing a shaper w/fq_codel a snap and work just fine on ubuntu. 

 [https://github.com/tohojo/sqm-scripts](https://github.com/tohojo/sqm-scripts)

see the sample files in /etc/sqm

---

### Post by jonathanese on 2018-08-20
Thanks. I already had looked at that exact one, so I went through with it.

A couple things were confusing, and I'm not sure where detailed documentation would be, but I got it up and running quite easily.

Thanks!

---

