---
title: "How to configure network for Static IP?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by jaydeepg on 2008-04-26
Hello all,  I am using the remix version of Hardy as my second distro, and the problem is related to this.  ( First is of course Plain Vanilla Hardy!!)

I am on an ISP that requires me to enter static IPs as well as DNS details.

Funny thing is when I right click on the network icon on the taskbar and select 'manual configuration', nothing happens.  It asks me to authenticate myself and then ... nothing.

This happened 3 or 4 times and then, I checked the output on a console.  It mentioned something like kcm_kdenetworkconfig not found or something like that.

Issue is if I cant configure network, I cannot donwload new packages, a catch 22 situation.  

Can someone help me?  I tried the manual config method mentioned in the sticky above, but it didnt work out.

---

### Post by kevdog on 2008-04-26
Need to more about the ISP requirements since I find it very unlikely you can just randomly assign yourself an IP address.  The ISP you give you the address, netmask and gateway address and also tell you any other requirements.

---

### Post by jaydeepg on 2008-04-27
Hi, when i say static ip I mean that I need to enter all these paramters too.  Issue is how and where? I am not exactly a newbie, and have been exclusively on linux for more than a year now.

---

### Post by kevdog on 2008-04-27
Put them in the /etc/network/intefaces file.  I believe Weiman01 has a post that instructs how to specifically do this.  If this doesnt work, try connecting manually (another stickie) to see if you can discover what the problem is.

---

### Post by jaydeepg on 2008-04-27
Hi thanks for the suggestion.  I will try this out now.  Just checked the interfaces file on my ubuntu install and it looks perfect, so am assuming that it should work.  How about the DNS settings? Where do they go?

---

### Post by kevdog on 2008-04-27
If you have the DNS servers, and you are not using dhcp, then you need to manually edit the /etc/resolv.conf file and add them (an example below):

nameserver 192.168.1.254
nameserver 202.54.1.20
nameserver 202.54.1.30

You can specify up to 3 nameservers.

---

