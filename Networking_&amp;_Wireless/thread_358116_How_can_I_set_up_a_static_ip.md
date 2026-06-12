---
title: "How can I set up a static ip?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by moreon on 2007-02-10
Hi everyone! My aim is to be able to configure linuxdcpp so that I can search and download. In order to do that I need to forward a port in my router, but before that, I need to set up a static ip address. Can anyone help me out? Bear in mind that I'm not experienced in networking :confused:

---

### Post by norman_ on 2007-02-10
If your ISP gives you dynamic ip, you're probably best going for a redirect service such as [www.dyndns.org](www.dyndns.org) 

It's free and easy to set up. I don't believe you need me to explain how. Just surf their site...

---

### Post by tturrisi on 2007-02-10
$# man interfaces
has the answer you need to config you comp for a tatic lan ip address.
/etc/network/interfaces

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255

[http://www.fileformat.info/tip/linux/dynamic2static.htm](http://www.fileformat.info/tip/linux/dynamic2static.htm)

---

### Post by moreon on 2007-02-10
norman_: I created an account in dyndns.com, got a hostname for my computer, and have ez-ipupdate running. What is my static ip address now so that I can put it in my router to forward a port?

---

### Post by tturrisi on 2007-02-10
> **moreon said:**
> norman_: I created an account in dyndns.com, got a hostname for my computer, and have ez-ipupdate running. What is my static ip address now so that I can put it in my router to forward a port?
(Note: the caps are for stress, not yelling)
You DON'T have a static ip address!
You need a static ip address for the LAN computer, a local ip address for your ubuntu comp.  When you port forward, you are forwarding the external request for some port to the LOCAL ip address of a comp on your LAN.  

Your isp assigns you a dynamic ip address.  Your router takes that dynamic address and uses network address translation and assigns a local only dynamic address to all computers on your lan except for the computers that use a local static ip address.  The reason you want the comp to use a static addres is so port forwarding always works.  If the comp used a dynamic ip and then the router assigns it a different ip down the line (and it will) then the port forwarding will break.

ddns handles the fact that you have an isp assigbed dynamic address and even if the isp assigns a different address then ddns will automatically pick up on that so your servers are still accessable using a fully qualified domain name.

read up at [www.portforward.com](www.portforward.com)

---

### Post by norman_ on 2007-02-10
I'm sorry, I guess I misunderstood your question. Read up on what tturrisi said. 

Dyndns only serves for other computers on the web to always be able to reach you at the same adress. It is a fake static-ip in that it sends all the traffic from that same adress to your changing IP. 

If you are wondering what IP your router has assigned to your computer, then that's something to read in the router's manual (or browse in the router's interface)

---

### Post by moreon on 2007-02-11
First of all thanx for all your help so far. I changed my network settings, by roughly following the guidelines for Mac OS in portforward.com, under System/Administration/Networking, so now my comp has the IP 10.0.0.50 (my router's address is 10.0.0.2). Then I forwarded a port in my router, again following portforward.com, to 10.0.0.50. So, after that, I configured dcpp to use the forwarded port and in the 'external ip' field I put my then current IP address but it still wouldn't work. Any ideas? I also was wondering how would it work, since my external IP address changes every hour (I think). Do I also have to configure any DNS servers under the DNS tab in network settings?

---

### Post by tturrisi on 2007-02-11
> **moreon said:**
> First of all thanx for all your help so far. I changed my network settings, by roughly following the guidelines for Mac OS in portforward.com, under System/Administration/Networking, so now my comp has the IP 10.0.0.50 (my router's address is 10.0.0.2). Then I forwarded a port in my router, again following portforward.com, to 10.0.0.50. So, after that, I configured dcpp to use the forwarded port and in the 'external ip' field I put my then current IP address but it still wouldn't work. Any ideas? I also was wondering how would it work, since my external IP address changes every hour (I think). Do I also have to configure any DNS servers under the DNS tab in network settings?
If port forwarding is setup correctly and dcpp is setup to use that port, then remote users should be able to connect to your computer using the fully qualified domain name assigned by dydns.  You may need to config dcpp "external ip" to be the router ip address 10.0.0.2. Not sure cause I never used this product, but I do know about port forwarding cause I do that for my servers.

---

### Post by fj34r on 2007-02-18
Interestingly enough, I used /etc/network/interfaces and configured a static IP.  It has worked until now, but for some reason now when I boot, it won't set the static IP.  Any ideas?

---

