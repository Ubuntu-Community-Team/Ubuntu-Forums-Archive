---
title: "Sharing DSL connection over LAN"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by sparkymat on 2007-07-23
Hi,

I am trying to share my internet connection over the lan. My network is configured as follows. The DSL modem and 2 Ubuntu machines are connected to a router. The primary Ubuntu machine dials and connects to the DSL modem (PPP). I was wondering how I can share this connection to the second Ubuntu machine. 

I had tried opening a SOCKS proxy on the second machine via SSH tunneling to the first one, but I couldn't figure out how to get apt-get or aptitude to use a SOCKS proxy. I need the shell to recognize the proxy since it's a headless machine. I know how to configure a http proxy in shell (the http_proxy environment variable). Is there something similar for a socks proxy?

I did read about articles on how to enable my primary Ubuntu machine as an internet gateway ([http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)) . However, I got the feeling that this tutorial was for a system with 2 network interfaces and how to reroute the interface connected to the local network. My problem is that I have only one network interface which connects to the router which in turn connects it to both the modem and the second machine.

I would appreciate any assistance on this problem. Thanks in advance.

---

### Post by Warren Watts on 2007-07-24
Can the router be configured to provide the needed PPPoE authentication instead of using the computer to do it?  Most routers can be configured for PPPoE Authentication.

That would allow the router to obtain the IP from your ISP, and distribute local IP's to each machine on the network.  Then every computer behind the router would have internet access.

Look thru your router manual, or visit the manufacturer's website for a HOW-To if you need help.

Warren

---

