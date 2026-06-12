---
title: "Sharing WiFi to Ethernet"
date: 2021-05-11
forum: Networking &amp; Wireless
---

### Post by dpclarke42 on 2021-05-11
Hello,
I have a computer running Ubuntu 20.04 with a wireless card and an onboard ethernet card. I would like to share the wifi connection to the ethernet in order to connect devices that don't have a wifi card. I'm currently attempting to connect a Linksys wrt 3200 to the ethernet via it's WAN port and it just won't get an IP address no matter what I do. I don't think Ubuntu is providing an IP and I can't seem to force it. 
I've followed every tutorial I could find but nothing works. As far as I can tell I should only have to add a new ethernet connection, go to the IPv4 tab, and select "Shared to other computers" but that hasn't worked. 

Thank you very much for any and all assistance.

---

### Post by TheFu on 2021-05-11
Internet Connection Sharing is probably really what you seek. I've never done it.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Since home routers do this stuff well, there is little reason for most people to need this anymore, so don't be surprised if there are hiccups trying to make this work.

Or you could turn your desktop into a router, but that has lots of security implications.

If it were me, I'd try to get my existing wifi router to do what I need instead. Most home routers provide DHCP which provides the network information and DNS to all clients - wired and wifi on request.  You can also setup static IPs for wired and wifi devices using the MAC as an identifier for which MAC ---> IP address on the LAN.

Of course, there could be physical issues which have you thinking this would be a good way to go.
The wifi-router is in a different part of the building and you have a number of local ethernet-only devices. I avoid using wifi whenever possible, so when I need to bridge from 1 floor of the house to another, I've used PowerLine ethernet devices. There are 2 in a "set".  1 gets connected to a wired ethernet port and plugged into the wall near it and the other gets placed anywhere else within the same building electrical circuits.  On the far-end, I connect either a computer or a switch if I have multiple devices that need connections.  The PowerLine ethernet "bridges" ethernet over the power circuits of the house. They come in different speeds, but just like wifi, the true speeds we get are much less than the side of the box claims.  I have a 600 Mbps version (advertised speed). On the same floor, it provided 220Mbps and between floors it does 62Mbps, which is very good for almost any need - it is certainly faster than my internet connection - up or down!

There is also MoCA which is also a bridge, but it works over COAX wires. This can be much faster, but it is only useful if your building has coax wiring.  They sell 2.5Gbps versions which actually provide 2.5 Gbps bandwidth that can be parsed out to different nodes 1Gbps at a time. It seems all the chips for MoCA 2.5Gbps are the same regardless of the vendor, so we don't need to worry much about brand names.

Both PowerLine and MoCA are very stable connections, unlike wifi. Wifi is a joke.  Claimed 300Mbps connections really get closer to 30 Mbps throughput here and I don't live in a crowded wifi area.  I have coax and if I were trying to bridge upstairs and downstairs again, I'd use moca adapters with a cheap 5 or 8 port switch on the end opposite the router.

Anyway, some options for your consideration.

---

### Post by dpclarke42 on 2021-05-12
ICS is what I'm attempting, and it's what's not working. I must not have been as clear on that as I thought. The link provided is one of the tutorials I followed and it just didn't do what it said it would do. I just moved into a basement apartment, and have to self isolate for two weeks as per provincial restrictions. My only internet access at the moment is wifi from upstairs, my sister's. I have one wifi card, which is in my media centre PC (Ubuntu 20.04). I want to share it's connection to my router so I can send it to my desktop, PS4, etc via ethernet. The ethernet port on my media centre connects directly to the WAN port on the router, but the router doesn't get a WAN IP and reports no internet connection. How do I get an IP assigned to the router, or any device connected to the media centre's ethernet port?

Long term, I very much plan on having a new connection installed specifically for me, but that obviously has to wait until after self isolation. In the meantime, I'd rather not live without internet on most of my devices.

Edited for spelling and grammar.

---

### Post by SeijiSensei on 2021-05-12
First possibility is that you did everything right but forgot to enable IP forwarding in the kernel. Edit the file sysctl.conf and set
```
net.ipv4.ip_forward=1
```
then run 
```
sudo sysctl -p
```
to have the kernel read the new setting.

If that doesn't work, then let's try this. Assign the router's WAN port and the ethernet port on the media center PC to static IP addresses within the same subnet, e.g., 192.168.1.1-255. Make sure the router's default route points to the PC upstream. On the PC, add a masquerading rule like
```

sudo iptables -t nat -A POSTROUTING -o wlan0 -j SNAT --to ip.addr.on.wifi

```
replacing ip.addr.on.wifi with the address assigned to the PC by the wifi service, and wlan0 with the name of the wifi interface on your machine.  (These days it can be something like "wlxec086b1841a7" rather than the simpler "wlan0" used in earlier kernels.) Run the command "ip addr" to see the interfaces on the machine and the addresses to which they are assigned. Make sure the PC's default route points to the wifi router upstream (that should already be the default).

---

### Post by dpclarke42 on 2021-05-12
Thank you very much for the reply! I very clearly recall at least attempting to enable IP forwarding, but it was commented out in sysctl.conf so I must not have done so properly. Regardless, that didn't work, so I set static IP addresses for the ethernet port and router. After running enabling masquerading with the snippet provided, (again, could have sworn I'd don't that already, several times, but I must have not done it properly). 
At any rate, it's now passing connectivity though the way I'd expected. Thank you very very much!

---

