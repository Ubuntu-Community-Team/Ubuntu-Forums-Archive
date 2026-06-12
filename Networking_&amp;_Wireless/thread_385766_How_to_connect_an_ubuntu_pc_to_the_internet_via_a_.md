---
title: "How to connect an ubuntu pc to the internet via a windows xp pc"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by wickyd on 2007-03-16
Hi folks

My network consists of:
1. A Windows XP pc with an external 56k US Robotics modem.
2. An Ubuntu 6.10 pc.
3. Ethernet hub connecting the two machines together.

The Windows XP box has the IP address of 192.168.0.1
The Ubuntu box has the IP address of 192.168.0.2

How do I connect to the internet from the Ubuntu box via the hub and through Windows XP?

Thank you.
wickyd

---

### Post by chewearn on 2007-03-16
Here are a general step-by-step what you need to do:

1. In WinXP, enable internet connection sharing
2. In WinXP, bridge the modem and ethernet port (if not automatically done during previous step)
3. In Ubuntu, use your WinXP IP as the DNS and Gateway IP

That's it.

---

### Post by wickyd on 2007-03-16
That sounds easy enough :) 

Thank you. I shall try it this evening.

---

### Post by wickyd on 2007-03-17
I did what you suggested and it works partially.

The ubuntu pc is a clean install of 6.10.
I can ping [www.google.co.za](www.google.co.za) from ubuntu, but it takes much longer to get a response.
I open up Firefox and try to go to [www.google.co.za](www.google.co.za) or any other site. 
It reads: Looking up [www.google.co.za](www.google.co.za)... and after a while it reads: Server not found.
In windows google takes a few seconds to load.

How do I fix this problem?

Thank you.
wickyd

---

### Post by HereInOz on 2007-03-17
You may have to enter the DNS server ip addresses which are used by your ISP into your network setup in Ubuntu.  It is possible that the XP machine is not providing proper DNS services, or the Ubuntu machine is not accepting it.

If you hard code the IP addresses of your ISP's DNS servers, then you may get things working.

---

