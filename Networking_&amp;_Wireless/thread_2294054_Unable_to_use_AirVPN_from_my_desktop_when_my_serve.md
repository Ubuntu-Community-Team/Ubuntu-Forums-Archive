---
title: "Unable to use AirVPN from my desktop when my server acts as DNS/DHCP"
date: 2015-09-09
forum: Networking &amp; Wireless
---

### Post by zoidberg2 on 2015-09-09
I'm using Ubuntu 14.04 on my Desktop &  server. I am unable to use Airvpn to connect to sites blocked by my ISP when I use my Ubuntu Server as my DNS & DHCP server.  
 

 When I power the server down & use my ISP router as the DNS & DHCP server I'm able to use Airvpn no problem but when I try doing with my server up running DNS & DHCP I'm getting messages that sites are blocked despite the fact Airvpn says it is now connected to their server.  

 

 When I google what is my public IP I'm getting an IP address similar to this 2a02:c7d:4e26:with 5 more octets, I'm assuming it is an IPV6 address) instead of my public IPV4 class that I get when I try searching for my public IP when the router is set up as the DHCP/DNS server. I'm getting this long IP address both when I'm connected & disconnected from Airvpn.      

 

 

 A few things I tried to resolve the issue was,
 I had set the computer as a static IP address, using it's MAC address I now have the DHCP server assigning it an IP address.  

 Deleted my history & cache in the browser.  

 Cleared my DNS cache 
 Restarted the DHCP & Bind services on the server  
 Changed my DNS forwarder IP to another DNS server
 

 Any help would be greatly appreciated.


*****Disable IPv6 fixes this issue **

To disable ipv6, you have to open /etc/sysctl.conf using any text editor and insert the following lines at the end:

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

If ipv6 is still not disabled, then the problem is that sysctl.conf is still not activated.

To solve this, open a terminal(Ctrl+Alt+T) and type the command,

sudo sysctl -p

You will see this in the terminal:

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

After that, if you run:

$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6

It will report:

1


If you see 1, ipv6 has been successfully disabled.

---

