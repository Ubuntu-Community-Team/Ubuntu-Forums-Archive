---
title: "Static IP"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by thault on 2014-05-28
How do I go about setting up a static IP for Xubuntu 12.04. Thanks for the help.

---

### Post by Bucky Ball on 2014-05-28
Right click on the network icon and 'Edit Menus' (this option is at the bottom of the left-click menu in 14.04, from memory).



* Click the wireless (or wired) and edit. Go to the IPv4 setting tab and set up the static IP in there; 
* Set 'Method' to 'Manual' (not auto);
* You'll need the router's (the gateway's) IP and for the DNS servers your ISP is using (probably). 

If your router is issuing IPs via DHCP, the best thing to do is set the router to issue IPs within a certain range and _make sure your static IP is outside of this range_ or switch off DHCP on the router, if that's possible (easiest). Either way, Very Important.

PS: The netmask is generally 255.255.255.0

---

### Post by thault on 2014-05-29
Why so I need the ISP's DNS? This is a LAN static ip?

---

### Post by Bucky Ball on 2014-06-01
Go ahead and try without the DNS. If you are on the LAN only and not intending to use the WAN (internet in the outside world) then it should work. If you are intending to use the WAN you probably won't be able to connect to your ISPs server. Give it a try and find out. Please post the outcome.

---

### Post by chili555 on 2014-06-01
> **thault said:**
> Why so I need the ISP's DNS? This is a LAN static ip?It doesn't necessarily need the ISPs DNS; it just needs *some* DNS. You may and you must specify any that you prefer.

When you get an IP address from the router by DHCP, you also get, among other things, DNS nameservers. If you specify the address instead, then you are also responsible for DNS. A valid option is the address of the router or switch; 192.168.1.1 or similar.

---

### Post by thault on 2014-06-07
I gave the DNS as the router for the network, 192.168.0.1 and it works beautifully.

---

### Post by Bucky Ball on 2014-06-07
Good news. Please mark as solved to help others. ;)

---

