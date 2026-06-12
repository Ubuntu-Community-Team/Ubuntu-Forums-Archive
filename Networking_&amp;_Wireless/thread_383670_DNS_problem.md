---
title: "DNS problem"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by b0rk on 2007-03-13
The DNS field in the Admin-Network box is set to 192.168.1.1 which is the IP address for my D-Link Router.  It gives me access to the router and I can even ping internet addresses but I cannot access any web sites.

If I change the DNS field to the primary server number provided by my ISP then it works fine for a short time then stops.  Logging back into Admin-Network I find that the number has reverted back to 192.168.1.1 and deleted the other.  

How can I prevent this happening? or is there another solution?

---

### Post by lloyd_b on 2007-03-13
What I suspect is happening is that DHCP (the process that automagically obtains the IP address and other information) is overriding your manually set nameserver.

Ideally, your router should be able to act as a nameserver, but it apparently isn't configured properly.

Three options:

1.  Configure the router to properly act as a nameserver.  Sorry, the specifics for how to do this vary from router to router, so I can't give detailed instructions.  One suggestion: In Firefox, put "http://192.168.1.1" in for the URL - with many routers, this provides access to the configuration.

2.  Change from DHCP to static IP/Nameserver configuration.  This can be done via the GUI, under Admin->Network.  

3.  Change the DHCP client configuration so that DHCP no longer controls the nameserver setting.  This can be done by editing the file "/etc/dhcp3/dhclient.conf".

Lloyd B.

---

### Post by b0rk on 2007-03-15
Thanks lloyd_b

 I had previously tried every configuration possible with my router, a D-Link G604T  and eventually updated the firmware.  This proved to be the answer, a new configiration page labelled DNS was added and I was immediately able to access the internet

Cheers

b0rk

---

