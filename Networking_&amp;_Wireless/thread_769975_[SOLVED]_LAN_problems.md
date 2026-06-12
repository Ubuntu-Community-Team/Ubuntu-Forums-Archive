---
title: "[SOLVED] LAN problems"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by kgriff on 2008-04-27
I am trying to set up an in-house network with two computers running Hardy.  (I also have multiple Windows machines running, but they&#314;l come later.)  In addition to networking the computers, I also want to access teh internet with both.  This post will probably be pretty long, but I want to provide enough information that somebody may be able to help me out.

So, here&#347; my setup:
My internet is DSL through Qwest.  I am using the Qwest provided Actiontech DSL router/gateway.  It is at IP 192.168.0.1.  This is in my basement.  In addition to the Actiontech I have a Belkin ¨Wireless G Plus¨ router at IP 192.168.2.1.  This is on the ground floor and was purchased to provide a wireless access point for a laptop.

With a plain jane setup, the Actiontech is the DNS for the Belkin, as well as for one computer connected to it wired. The Belkin is the DNS for a computer connected to it wired, as well as the wireless laptop.  (Although this may seem like a strange setup, it is necessary.  If I enable wireless on the Actiontech, I don´t have enough signal strength for a reliable wireless connection)  with this configuration all computers can access the internet.

The wired computer attached to the Actiontech is IP 192.168.0.4.  The wired computer attached to the Belkin is 192.168.2.2.  This, I believe, is the root of my failure to network.  I have had a successful network running, but only if I take the Belkin out of the mix and connect both computers to the Actiontech.

With my current setup, the machine at 192.168.2.2 can ping 192.168.0.1 and 192.168.0.2, but 192.168.0.2 cannot ping 192.168.2.2.  Using VNC, 192.168.0.2 cannot even see that there are any other computers on the network, (using the default Hardy installed Remote Desktop Viewer)  However, 192.168.2.2 can connect to 192.168.0.2 by IP, but not by name.  The connection is immediately dropped, though.

In addition to the one-way ping, computer 192.168.2.2 can connect to the Actiontech at 192.168.0.1, as well as the Belkin at 192.168.2.2.  However, computer 192.168.0.4 can only connect to the Actiontech.

Here¨s what I¨ve tried to make this work:
* Set Actiontech DHCP IP Range to 192.168.0.2 thru 192.168.0.25, then set Belkin IP to 192.168.0.40.  According to the Belkin manual, this can be done.  However, once I have completed this operation, I cannot connect to the Belkin by entering the new IP in my browser.  This forces a reset to factory settings.##

* Turn off Belkin firewall.

* Configure Belkin as ¨Access Point¨.  According to the manual, this disables DHCP and NAT IP Sharing.  I have to manually set an IP on the same subnet as the rest of my network.  In this case, I have tried setting IP 192.168.0.40, 255.255.255.0, as this IP is above the range that should be automatically assigned by the Actiontech.  This kills my internet connection for the machine connected to the Belkin, doesn´t fix my LAN issue, and again forces a reset to factory settings on the Belkin.##

##According to the Belkin manual, in both of these cases, I should be able to communicate with the Belkin router by using the newly assigned IP in my browser.  This doesn´t seem to work, though.

I do have all machines assigned to the same Domain.

If anybody has any ideas how I might get this working, I´d sure appreciate it.  I´ve spent several hours playing with settings, but haven´t gotten anywhere.

---

### Post by helgman on 2008-04-27
OK, here we go (since your post was pretty long, my answer will be ...)

When using IP, two parameters are used, IP-address and subnet mask. When your home router default to a 192.168.x.x address you can assume that the subnet mask default to 24. For more information about this, take a look in Wikipedia or any other source that can give a quick explanation of basic IP-networking.

Normally, different subnets don't mater ... as long as you use IP and have routers forwarding the traffic the computers will communicate (provided they have correct routes etc). And here's your problem. Assume that the computers (and the router) that has addresses beginning with 192.168.0.x (192.168.0 is the network address) is LAN1 and computers with an address of 192.168.2.x (192.168.2 is the network ...) is LAN2.

A) Computers on LAN2 has the AP (Belking) as default gateway, that is, all packages that are not destined for LAN2 (going to LAN1 or the Internet) is forwarded to the AP and the AP then forwards them out it's "WAN"-interface (as opposed to LAN-interface 1 through 4 or whatever it is on your model).

B) Computers on LAN1 has the Actiontech as default gateway, that is, all packages that are not destined for LAN1 is forwarded to the Actiontech and the Actiontech then forwards them in the same manner as the AP upstairs.

Problem 1: If computers on LAN1 should be able to connect to computers on LAN2 (not the other way around), then will have to have a route to LAN2, that is, they must know where on LAN1 to send the packages that should be forwarded to LAN1. Actiontech won't do it since Actiontech forwards the packaged to the Internet. It's the AP that should forward the packages. So in order for a computer on LAN1 to be able to send initiate communication to LAN2 it needs a route, using the *route* command, for example or one of the fine graphic tools in Ubuntu.

Problem 2: Most home "routers/gateways/APs" has a default PAT (often called NAT) function that translates (changes) the address as it traverses the device from the LAN to the "Internet". Computers on LAN1 never sees the IP-address of computers on LAN2, all they see is the IP-address of the AP and trying to connect to LAN2 IP-address from LAN1 will simply not work (there should be some fairly good articles about this on the Internet).

This is what I would do:

1) Disable all DHCP etc in the Belkin and set an address in the 192.168.0-range.
2) Connect the Belkin to the Actiontech via LAN-ports on both devices.
3) Reconnect all computers (re-associate the wireless clients) and make sure that every device now gets an IP-address from the Actiontech.
4) Cross my fingers and hope that they all play nicely.

I hope this helps ...

Regards,
Helgman

---

### Post by kgriff on 2008-04-27
All is good now.  Apparently, that finger crossing really works.:)
The step I was missing was to connect the Belkin to the Actiontech via one of the Belkin LAN ports.  I was still connecting it via the WAN port on the Belkin.
Reconfigured the Belkin. connected it to the Actiontech using the LAN port, and it was all downhill from there.
Thanks, Helgman.

---

