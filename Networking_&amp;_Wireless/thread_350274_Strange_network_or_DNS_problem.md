---
title: "Strange network or DNS problem"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by ethomas on 2007-01-31
Hi,

To celebrate the release of Windows Vista I installed Ubuntu 6.10 on my laptop last night. It all went perfectly but the networking exhibits a strange fault. I can ping any host and it works perfectly, but using Firefox or wget to retrieve a web page leaves the system trying to connect to the ip address "0.0.0.1".

To reiterate, Ping will connect to any hostname perfectly, with the correct ip address, but trying to use any web browser, or any more complicated tool always resolves the hostname to 0.0.0.1.

I have used many linux systems in the past, and have a pretty good knowledge of how they work, but with this I don't even know where to start. Rebooting into XP works fine, and my other PC which has 6.06 on it works perfectly on the same wireless network. Ping works for any hostname and so does connecting to an IP address, so the network connection seems fine.

The laptop is an Intel Centrino based Fukitsu Siemens Lifebook 7120.

Thanks,

Edward

---

### Post by ethomas on 2007-01-31
A quick update and correction. The system actually tries to connect to 1.0.0.0 (0.0.0.1 was a typo, sorry).

I have also tried connecting to the router with ethernet and it has the same problem. I discovered something else. By pinging a host, it will get the correct ip which then means I can go there in my browser and it will work (for that host only) temporarily.

Cheers,

Ed

---

### Post by mayonaise15 on 2007-02-01
Hey Ed,

sounds to me like you may not have any DNS servers set up?

Can you go to System > Administration > Networking, open up the DNS tab and see if there are any entries in there?  If you need an address to put in there 4.2.2.2 usually works and sometimes your default gateway will (possibly 192.168.1.1 or 192.168.0.1).

---

