---
title: "Need some help with home network"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by ltmon on 2005-11-22
Hi All,

For various reasons I need external access to my home apache server for one day only (tommorow).  I have apache running nicely, and a dyndns account set up that now resolves to my adsl address.

My setup is fairly common:

Ubuntu PC -----> NetgearRouter -----> ADSL Modem

Now I need to do two more things:
- Configure my PC with a static IP instead of DHCP
- Configure my router and modem to forward requests on port 80 to my PC

Unfortunately I can't get either of these things to work.

Firstly with static IPs:
Using the System/Networking tool I turn of DHCP and assign an IP to my pc outside of the range of my routers DHCP server.  From then on, none of my networking works.  I can't ping the router.  I can't ping any external site.  It stays this way until I re-enable DHCP.

Next with the port forwarding:
Ignoring the static IP I just tried to check if the port forwarding worked.  It doesn't.  I set both my router and modem to forward port 80 to my current IP address, but whenever I browse to my external address I am directed immediately to the ADSL modems administration console.

Any help with this would be much appreciated, as I would really like this to work.

THanks,

L.

---

### Post by Sheco on 2005-11-22
You have to use an IP inside the subnet of the router.

If the router's network is 192.168.2.x you have to use that subnet too. if the router has the entire subnet assigned to DHCP you might have to change that to avoid collitions.

About the port forwarding, you should check the router manual.

---

### Post by ltmon on 2005-11-22
Thanks for the help.

I just got to work and tried again from here: suprise suprise, the port forwarding works just fine.  It just doesn't work on the local network.  I guess that makes sense else how else would I ever reach my router configuration screen again if every port 80 request went to my PC.

As for the static address, you may need to hold my hand for a little while longer.

I see that my "Subnet Mask" is 255.255.255.0.  Does this mean that it is entirely assigned DHCP?  Am I even looking at the correct setting?

The other one I noticed is that the "Available IP addresses" were 192.168.0.1 to 192.168.0.5 (it's a 4 port router).  Is this something possibly in need of adjusting also?

Thanks,

L.

---

### Post by Sheco on 2005-11-22
DHCP is just a service that automatically assigns IP address to the computers connecting on the LAN, that's all it does.

subnet mask is the filter that specifies how big the subnet is.
255.255.255.0 means the subnet can contain IPs from x.x.x.0 to x.x.x.254, the router can take one of those and assign dynamically more IP addresses via DHCP, available IP addresses might be DHCP's range, you can use a static address outside that range (in the same subnet as specified by the subnet mask).

You can use 192.168.0.100 for example, and everything'll be ok, as long as DHCP doesnt try to assign somebody that IP, it's ok.

---

### Post by ltmon on 2005-11-22
[QUOTE=Sheco]DHCP is just a service that automatically assigns IP address to the computers connecting on the LAN, that's all it does.

subnet mask is the filter that specifies how big the subnet is.
255.255.255.0 means the subnet can contain IPs from x.x.x.0 to x.x.x.254, the router can take one of those and assign dynamically more IP addresses via DHCP, available IP addresses might be DHCP's range, you can use a static address outside that range (in the same subnet as specified by the subnet mask).

You can use 192.168.0.100 for example, and everything'll be ok, as long as DHCP doesnt try to assign somebody that IP, it's ok.[/QUOTE]

Hmmmm.
Well I did try assigning my IP as 192.168.0.50 (which like your example should be fine I think) and the error still occured then.

I did notice however that the "Available IP addresses" field in my router config then updated itself to allow all ip's between 192.168.0.1 and 192.168.0.50.

L.

---

