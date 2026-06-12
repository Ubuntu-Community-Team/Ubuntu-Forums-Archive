---
title: "can't connect to router"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by sang froid on 2008-01-19
I've installed Xubuntu onto my desktop and I have it connected by an ethernet cord to a 2Wire 2700HG-B router. I've configured the DNS in network settings and changed the connection to DHCP and ran PPPoE programs but it still won't connect. I've been looking for hours for a solution... can anyone help me?

---

### Post by HermanAB on 2008-01-19
Uhmmm, 2Wire 2700 is a integrated DSL Wifi NAT router.

You have to configure your ethernet adaptor with DHCP only, not PPPoE or any other cruft.  Once you get an IP address from the router, you have to launch a browser (Firefox) and try to go somewhere on the net.  Your ISP will then divert you to a sign-in page and once you have registered, things will start to work right.

So, run your network wizard thingy and enable DHCP, then let it do its thing.

Now do a bunch of low level tests to see what happened:

Verify that you actually got an IP address, and that the port is up:
$ sudo ifconfig eth0

Verify that you got a DNS or three:
$ cat /etc/resolv.conf

Verify that you got a gateway address (Look for UG next to an IP number):
$ sudo route

Test the internet connection through the NAT router by pinging the DNS:
$ ping server.ipaddress.from.resolv.conf

If all of the above are OK, then run Firefox and try to go somewhere, Yahoo, CNN, whatever - you will be diverted to your ISP login screen.  Register the MAC address of the router and life should be good.

Hope that helps!

Herman

---

### Post by sang froid on 2008-01-20
Ok the router works now. It was a connection issue I guess, the router was being difficult. Thanks for your time

---

### Post by racurtis on 2008-06-08
I'm having a similiar issue.  Each time I restart my Xubuntu system my DNS settings change.  I'm on a 192.168.1.X network, however, each time I restart my DNS server setting changes to 192.168.0.1.  Once I manually change it (either in the Network Settings or by editing the /etc/resolv.conf file) and then restart the interface everything works peachy.

I've set up my eth0 interface with Roaming OFF and a static IP with a subnet of 255.255.255.0 and a default gateway of 192.168.1.1.  Not sure what's going on.  Any suggestions?

---

