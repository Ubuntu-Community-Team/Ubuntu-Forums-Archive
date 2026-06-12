---
title: "Changing IP Address, New ISP, Static to Dynamic"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by efreedom on 2007-06-09
I have Ubuntu set up to be my firewall router box.

Internet --> Modem --> Ubuntu Box --> Switch --> Various Windows and Linux Boxes

Originally the modem was ADSL and provided a static public IP address to the box

The Ubuntu Box has 2 NIC cards. 
On the modem side was the static public ip address
On the switch side, the IP was internal, dynamic ip address provided by dhcp on the Ubuntu box

I used iptables to handle the mapping for access, firewalls and routing.

That worked great.

Then, I had to move. The new location doesn't have ADSL available so I had to switch the modem to a Cable modem. Two issues I need to resolve:

1) Switching the IP address to the new value
2) Reconfiguring the system to use a dynamic IP address provided by the ISP (Comcast)

My first thought was simply to change the values in the interfaces file and reboot the box. As I was entering the values, I also realized I needed to change the DNS IP in resolv.conf. So, while I can see the current temporary values for the IP address, network mask and gateway from my temporary router, I have no idea what values to use for the DNS resolution.

Once I get past the issue of the DNS resolution (and assuming it works), I then need more information on how to configure the external NIC card to accept a Dynamic IP address from the ISP.

The new modem is a Motorola Surfboard 5100. I'm using the ethernet connector rather than the USB
The switch is a straight forward 8 port 10/100/1000 switch from netgear

Any ideas to get me started in the right direction would be appreciated.


Bob

---

### Post by nixfaced on 2007-06-09
Hi, probably the easiest way for you to fix this is to edit /etc/network/interfaces.  You didn't mention which interface was internal and which was external, so for example purposes we'll say eth0 is your external interface.  You'll want the following lines:

iface eth0 inet dhcp
auto eth0

Delete the other address/gateway/etc information from that section.

Then do:

sudo invoke-rc.d networking restart

(It's quicker than rebooting...)

That'll grab you an IP address from comcast.  It will also put the correct nameservers in resolv.conf for you.

Hope this helps.

---

### Post by SyberKowboy on 2007-07-24
I'm dealing with a similar problem. Whenever I switch from one network to another i.e. from Home to Work I do not recieve DHCP until I restart the system. I've tried restarting eth0 in a number of ways but still no DHCP. Any body have any ideas? TIA

---

