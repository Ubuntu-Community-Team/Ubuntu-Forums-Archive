---
title: "Port Blocked in Ubuntu but not Windows -- Same Machine!"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by gilf on 2008-01-27
This has really got me puzzled:

This happens on the same Ubuntu machine either dual booting to Windows, or even running Windows in a virtual machine while Ubuntu is up. Attempting to connect to a router's html interface via Firefox

1.) never works in Ubuntu
2.) always works in Windows

The interface address is:

169.254.1.26   port  8180

I type **[http://169.254.1.26:8180/](http://169.254.1.26:8180/)** I copy and paste it into the address bar in the same  browser on both OS, running concurrently in the same machine with the same network card, and the Windows browser connects and the Ubuntu one doesn't.

What gives?

Likewise I can ping 169.254.1.26 from Windows, but not Ubuntu. Again, on the same machine.

Output of:

sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Can anyone help?

---

### Post by jackocleebrown on 2008-01-27
As you cannot ping, I would say that this is more of a general network problem than a specific port blocking problem. Are you sure that your network connection is working on Ubuntu, can you ping anything else??

Jack.

---

### Post by kevdog on 2008-01-27
if you could list 

iwlist scan
ifconfig
lshw -C network

That would help us a lot

---

### Post by gilf on 2008-01-27
Thanks jackocleebrown, and Kevdog,

Yes,you're right, the port couldn't have been the problem -- of course, if the ping also wasn't working it would have to be an IP address problem. Yes everything else was working correctly -- internet, networking between workstations, samba, printing, even samba shared folders on the host and its virtual machine guest (windows). 

This was all going on in the 192.168.x.x LAN (static IPs). The WAN gateway was 169.254.1.x, and that was the address of the configuration utility as well. That was the only thing that didn't work, and* in Ubuntu only*, not windows.

I received a PM earlier that suggested that 169.254.x.x address space was used by zeroconf and there might be some conflict. So I took a chance and switched the address of the router to the 192.168.2.x range, and* it just worked!*

That doesn't absolutely confirm the zeroconf theory, but it does get things working correctly, so I'm going to leave it at that, with a good liklihood the PMer hit it on the head.

Thanks again Kevdog and jackocleebrown. And especially to. . . ., well you know who you are!

---

