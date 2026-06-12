---
title: "DNS problem"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Alex74447 on 2007-06-09
Hi, guys. I'm relatively new to linux and also networking. My problem is as follows:
I am able to successfully ping websites such as google, I am able to communicate with the router, I am able to type in "64.233.169.104" in firefox and get google, and finally, I can use the internet on a laptop (It's set up through a router.) I read somewhere that this may be due to a DNS setting problem. I'm not sure where or how to set up the DNS settings properly. In the network settings under the DNS tab and under the DNS Servers list there is nothing so I don't know if that's a problem. Under the search domains theres just some comcast address. (My ISP) Any help would be appreciated, thanks!

---

### Post by HereInOz on 2007-06-09
You probably need to get your DNS addresses from your ISP, and then enter them in the DNS section of your networking utility. 

Some routers do not pass DNS information correctly to Linux, and this is the way around it.

Just a question - are you able to ping google by domain name?  Like ping [www.google.com?](www.google.com?)

If so, you may need to go in to Firefox, type about:config in the address bar, and turn off IPv6 support.  That may help as well.

---

### Post by Alex74447 on 2007-06-09
No, pinging the actual web address gives me an error right away.

Next I'll try copying the DNS settings from my other computer.

EDIT: Fixed! I just had to add 192.168.0.1 which is my router, I believe.

---

