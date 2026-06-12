---
title: "Dns"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by guilleme on 2011-02-16
A simple-dumb question, but one I couldn't find the answer to :) :
How do I change the DNS in ubuntu 10.10?
The DNS the company that gives me the internet service provides is (a cr*p), very unefective, so, I want to change it, that's it.
 Thanks!
  (you know, I feel more-than-less dumb in regard of the fact I'm asking this. This is supposed to be easy, isn't it?)

---

### Post by lisati on 2011-02-16
I use [OpenDNS]("http://www.opendns.com/"), who have instructions for a variety of modem/routers. A link for using it with Ubuntu can be found here: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

---

### Post by Paqman on 2011-02-17
If you're connecting through a router then you change the DNS in that, not in your local machine. Go to the control page for that router and there should be a DNS setting in there somewhere.

---

### Post by donato roque on 2011-02-17
Right click the network manager on the top panel. Choose edit connections. Put focus on Auto eth0 or eth0. Choose edit. Go to iPv4 tab. The drop down field should have DHCP addresses only. Just enter the DNS addresses below.

If you are using Ubuntu 10.10 you should be set after you apply the changes. This will be saved. Ubuntu will use the new DNS address/addresses.

---

### Post by Keiran230 on 2011-02-18
Google offers a couple free, public DNS servers.

Primary Nameserver: 8.8.8.8
Secondary Nameserver: 8.8.4.4

One method to change the setting is to edit resolv.conf with
**sudo nano /etc/resolv.conf** (harder method)
or
**sudo gedit /etc/resolv.conf** (easier method)

---

### Post by guilleme on 2011-02-20
Thanks. ;).

---

