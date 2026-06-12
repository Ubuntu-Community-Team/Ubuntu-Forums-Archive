---
title: "internet problems"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by Dave Loschi on 2006-07-17
Hello!

After installing Ubuntu 6.06 I tried to configure the network settings.

As I have a router I only could choose "static ip" at the eth0configuration menu.

Then I typed in
subnetmask: 255.255.255.0
gateway: 192.168.123.254

My problem is that I do not know what to type in at the ip-adress field, because at winXP I had a dynamic ip.

I typed in 192.168.123.1 and later I started Firefox hoping it would find my router.
Fortunately Firefox find my router but if I type in a webadress, it can't find the site.
(the router is already configurated from a second computer and works perfectly)

What can I do?

Thanks for help
Dave Loschi

---

### Post by wahman143 on 2006-07-17
Hi,
If you are using a router AND you used DHCP on Windows, there should be no reason you cannot do so on Ubuntu as well.  

Can you ping any websites?  If not, can you ping the IP of any websites (ie - google will translate to 64.233.187.104)?  If you cannot ping by name but CAN ping by address, you need to setup your DNS in /etc/resolv.conf.  Your name server will be the IP Address of your router.

HTH,
W.

---

