---
title: "DNS disapperance on thumb drive ubuntu"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by Salisbury Satan on 2007-06-22
I've been runing xubuntu 6.06 on my laptop for about a year.  I like is so much that I decided to install xubuntu 6.06 on a usb stick (following the steps outlined on [www.pendrivelinux.com](www.pendrivelinux.com)).  Everything worked great and I now have my own personally configured ubuntu on a wee little thumb drive that I can take with me anywhere. :D

Now I come to work this morning and pop my usb stick into my desktop computer, and the DNS no longer works.  I can ping/ssh based on IP address just fine.  But 'ping google.com' results in an "unknown host" response and 'nslookup google.com' results in "parse of /etc/resolv.conf failed".  

Here's where it gets weird.  My laptop connects to the network just fine, with no dns troubles at all.  So I boot my laptop from the thumb drive, and I get the same errors.  Then I mount the laptop's hardrive and copy over all the network configurations to the thumb drive: /etc/resolv.conf, /var/lib/dhcp3/dhclient.*.leases /etc/dhcp3/dhclient.conf.  Still doesn't work.

So I've got a xubuntu 6.06 install whose dns worked yesterday, which doesn't work on either of two computers, even when using the configuration files and exact hardware of a xubuntu 6.06 install that does work. 

Can you see why I am baffled?  Anyone have any suggestions?

Thanks in advance.

---

### Post by Salisbury Satan on 2007-06-22
Sure enough, *after* I post, I figure it out.  It was a permissions problem.  /etc/resolv.conf was readable only by root.  (How it got that way is still a mystery, since everything worked fine yesterday).  Everthing is fine now, though.

---

