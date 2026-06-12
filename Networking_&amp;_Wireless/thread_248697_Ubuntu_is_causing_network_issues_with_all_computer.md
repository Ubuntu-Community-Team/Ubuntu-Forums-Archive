---
title: "Ubuntu is causing network issues with all computers on my home network"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by ExoticFish on 2006-09-01
So I have my main computer dual booting with Ubuntu and Windows XP.  I also have an Apple Powerbook on the same network.  All are going through a router to my DSL connection.

When I'm booted into Windows everything is happy but when I'm booted into Ubuntu (6.06) the network has weird problem with latency and packet loss.

I had an old SMC router that was I would have to release/renew the DHCP address from the DSL modem in order for Ubuntu to be able to access the internet.  Then after a few minutes the latency out to the internet (google in this case, which is normally around 40ms) starts jumping all over the place and then kept getting worse until i was getting 800ms response times.  I have borrowed a newer D-Link router and have that setup now.  It's working much better but I'm still seeing varying response times of up to 200ms and random packet loss.

I've read about people having weird issues with ipv6 turned on, but my Mac has had ipv6 for years without issue.  Anyone have any ideas?

---

### Post by Uluen on 2006-09-01
What's the output of ```
ipconfig /all
``` when in XP and ```
$ route
``` in Ubuntu?

---

