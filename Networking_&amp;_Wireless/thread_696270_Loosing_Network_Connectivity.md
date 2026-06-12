---
title: "Loosing Network Connectivity"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by pyromithrandir on 2008-02-13
I recently got a friend of mine to install Kubuntu on his desktop. So, he starts up and everything is fine, but after a while, his network connection stops working. That is to say, he can't even ping anything. I was over at his place the other day, and I tried doing some of the usual things that I do to get network connectivity back, like running dhclient and ifdown eth0 followed by ifup eth0. I also tried setting up a static IP so that he wouldn't have to deal with dhcp, if that was the problem, but all to no avail. I can't figure this out. It works just fine after a restart, and I know that it isn't the hardware, because it works fine on his Windows install (which is what he's mostly using due to this :( ). 
Anyone know how I can get this to stop happening, or even how to get the network back up?

---

### Post by gimfred on 2008-02-13
You are going to need to post the results of ifconfig, lspci at the very least to give people some information as to what they are dealing with. 'lshw -C network' would be a good idea too.

---

