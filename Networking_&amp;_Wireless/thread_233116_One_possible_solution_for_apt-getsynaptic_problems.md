---
title: "One possible solution for apt-get/synaptic problems"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by philosophersean on 2006-08-09
I was beating my head against the wall, trying to figure out why Dapper was giving me connection errors with apt-get update. I could point my browser to the repository and connect just fine; If I ran apt-get it would Err. It seems that my DD-WRT router firewall was the problem.

**The solution to my problem was to make sure my firewall wasn't blocking proxies. I had enabled this superfluous feature under my router's settings.**

Anyone having errors while updating your Ubuntu distro, double check to ensure that a firewall option isn't the cause. Taking five minutes directly attach your computer to your modem could save hours of headache.

---

### Post by drtvasudevan on 2006-08-09
could you tell us how you disabled it?
i appreciate this posting. a possible fix suo moto.

---

### Post by philosophersean on 2006-08-10
It was quite simple.

1. I connected to my router via the web interface (pointed my browser at it's IP address, 192.168.1.1)

2. I entered in the login/password information for my router

3. I clicked on the security tab.

4. There were several firewall options that are not enabled by default. I removed them all, and ran apt-get update.

5. I enabled a feature and ran apt-get update to check for errors.

6. I repeated step 5 until apt-get broke. 

7. Knowing which feature was stopping apt-get from running (In my case, "Filter Proxies"), I decided that I could live without it and left it disabled.

Hope that helps.

---

### Post by drtvasudevan on 2006-08-10
thanks!

---

