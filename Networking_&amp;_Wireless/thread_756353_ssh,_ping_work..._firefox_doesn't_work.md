---
title: "ssh, ping work... firefox doesn't work"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by arguellodw on 2008-04-15
I am connected via ethernet to my the network in the office.  I have been able to ssh to other hosts in the building, and I can ping these hosts and even ping google and other sites.  Firefox won't connect to any web servers though.

Running Gutsy 7.10 on an HP Pavillion laptop.  Any ideas?

---

### Post by Gen2ly on 2008-04-15
I believe firewalls can allow pings but still deny http ports, why a network would disallow this I have no idea.  Is links or lynx or elinks install on the pc?  try them to access a page and see this this is not a problem with firefox.

---

### Post by superprash2003 on 2008-04-15
you could try changing your DNS servers to opendns - [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by arguellodw on 2008-04-16
There is not a firewall up on the network, so I don't think that any access is being denied to firefox.

New info:
I can connect to the web servers within the subnet, but nothing outside of the subnet.

When I run 'nslookup danpc' (my laptop) from another network node, it replies with correct information.  When I run 'nslookup danpc' on my laptop, it replies that my server IP address is XXX.XXX.XXX.1#53, where X is a valid digit.  I don't know why the pound sign appears in the nslookup response.

---

### Post by Bosk22 on 2008-04-16
Perhaps your office uses a proxy in order to connect browsers within the subnet to the world wide web - Have a look at the 'network setting in Firefox' on a box that works and compare this with your own settings.

In firefox this can be found in edit/preferences/advanced/settings

Bosk

---

### Post by arguellodw on 2008-04-16
Problem solved!!
So, the moral of the story is double check your numbers.  That is, make sure the IP address of your gateway is correct.  While your at it, make sure that the computer is plugged in and the switch is at the 'on' position.  duh! =)

---

