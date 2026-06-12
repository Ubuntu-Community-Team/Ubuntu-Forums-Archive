---
title: "Slow vpn connection with network-manager-vpnc"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by dngpng on 2006-11-02
I'm using edgy now and need vpn to use the wireless network of my university. I installed vpnc and also compiled vpnc plugin for NetworkManager from cvs. The vpnc command-line works fine while it just consumes significant cpu load when transferring data with a relatively hight speed (e.g. 1MB/s).

The problem is, when using the NetworkManager to connect vpn, it prompts no error but the response of the connection seems to be very slow. For instance, the command "route" or "netstat -r" both start to show results after around 5 seconds; When ping some address, the time is also twice slower than that using vpnc directly. To open a webpage in this case is therefore annoying and I often got a timeout result.

I've checked /var/log/syslog but didn't catch anything useful. Any ideas?

---

### Post by alaman on 2006-11-02
try netstat -rn to see if the delay is with dns resolving

---

### Post by dngpng on 2006-11-02
> **alaman said:**
> try netstat -rn to see if the delay is with dns resolving

Thanks alaman, you really gave me a good hint. Then i figured out my problem was because in the file /etc/resolve.conf there were two dns servers, the first of which was not accessible after connected to vpn. 

So just simply adding a static route that redirect the access to the dns server through eth0 will solve the issue. (I guess to change the order of the two dns servers would also work.)

Well, seems the vpnc plugin for NetworkManager doesn't provide a way to run some script before/after the vpn connection. I'm wondering if there is a method to change route table or resolve.conf using this plugin to make everything automatic.

---

