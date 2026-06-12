---
title: "pinging hosts and accessing web servers"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by jbaker on 2006-11-04
Hello,

I have since figured out my network interface problem. One of the cards were bad. Any way I am asking if any one knows why I am not able to ping the only other host on my network.

I have a Dlink DI-624 Router with a Win XP pro machine and my ubuntu server. Here is a copy of my hosts file.

127.0.0.1       localhost
192.168.0.48    ubuntukb9
192.168.0.43    angel
192.168.0.1     gateway
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Here is my problem...from my win xp box aka angel I can ping the server and default gateway but from the server cant ping by either host name or ip my win xp box. Using my ubuntu box I can also ping google.com with success. How can I get my ubuntu server first to ping the other computer on my network.

My next problem is trying to get my web server out on the net... Using therouter stated above I have configured the dmz for my ubuntu box, and configured the virtual servers for the ports and daemons I want to use but still cant get any one to view the default web page on my server.. Any help would be greatly appreciated...

---

### Post by spd106 on 2006-11-04
When you went through the server hardening did you mis-configure a firewall rule? It's probably worth checking them over. Is it also possible that the router could be blocking pings from the DMZ? Have you tried arping instead?

Be aware that some ISPs block ingress web traffic, this can usually be avoided by moving from port 80 to another port.

---

### Post by jbaker on 2006-11-04
As of yet I havent installed a firewall on my ubuntu box. Any ideas for a good quality firewall for it? Now because I use verizon fios it blocks port 80 so what i have done is move my sites from ports 80-83 to ports 8000-8003. Any way you could go into a bit more detail on "arping"?

Thanks for your help in advance.

---

