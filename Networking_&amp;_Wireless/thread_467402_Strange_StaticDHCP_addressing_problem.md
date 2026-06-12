---
title: "Strange Static/DHCP addressing problem"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by Honig on 2007-06-07
I have a 6.06LTS server that I am setting up for a wireless gateway. I need one of the two interfaces on the box to have a static IP address. Out of the box 6.06 used DHCP and got an IP address from my network which was fine until I got SSH installed and everything updated. 

When I got everything to the point I needed to setup the gateway software I disabled the DHCP address in /etc/network/interfaces for eth0 and setup the network to be static using the correct address out of my IP pool. I restart networking and it responds at the new static ip address I setup for it. Great!

I work on the server through SSH for a little while and everything is fine. I get up and leave my desk for a bit to work on another project for a little while. I sit back down and try to reconnect to the server at the static ip address via SSH. No response. So I try pinging the address. No response. On a whim, i pinged the old DHCP address and poof got a response. So I tried to connect via SSH to the old DHCP address and whadoyaknow it connected and is my new server. 

At this point I am thoroughly confused as to WTH is going on, if I leave the server for a little while eth0 reverts back to the DHCP server even though the /etc/network/interfaces is correct. A simple reloading of the networking service sets it back to the static IP address, but that is not a long term answer to the problem. 

What is going on? What do I need to do to get this thing to stay on the IP address I give it in interfaces? 

EDIT: Also the server is not rebooting; uptime reports that it has been on for 17 days which is correct. 

Thanks in advance.
~J

This is my /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# DHCP Commented out 06/06/07
# iface eth0 inet dhcp
# Static IP Added 06/06/07
iface eth0 inet static
address 204.xxx.xxx.xxx
netmask 255.255.255.0
network 204.xxx.xxx.xxx
broadcast 204.xxx.xxx.xxx
gateway 204.xxx.xxx.xxx

```

---

### Post by nixfaced on 2007-06-07
I'll take a crack at this...

I suspect that dhclient is still running, assigning your old address, even though you changed /etc/network/interfaces and restarted networking.  

I attempted to duplicate your actions here, switching from dhcp to static and restarting networking, and noted that dhclient was still running afterwards.  

So I then ran dhclient -r  manually, which should release the IP and then *cause the client to exit*, according to the man page.  As far as I can tell, /etc/init.d/networking restart calls ifdown, which in turn runs dhclient -r.  However, dhclient  releases the IP, but the dhclient does not exit -- it continues to run.

So, just for ha-ha's, check your process list and see if dhclient is in fact there.  If so, that's probably the issue, which you should be able to fix by sudo kill -TERM and networking restart.

I am not 100% sure that this is the actual problem, because to verify it I'd have to go from dhcp to static and then wait around to see if dhclient grabs another lease when the old one expires, and that's more time than I'm willing to put into this atm...  It seems to make sense, though, and I can't think of another reason for your server to get its old IP back.  If so, I guess it counts as a bug.  I've seen many posts describing a similar problem to yours, too.  

Hope this helps.

---

### Post by Honig on 2007-06-08
> **nixfaced said:**
> 
I suspect that dhclient is still running, assigning your old address, even though you changed /etc/network/interfaces and restarted networking.  

Hope this helps.

That was the issue. I killed the process and we will see what the result is. I'm fairly certain that it should be quashed. 

Thank you for taking the time to answer!
~J

---

