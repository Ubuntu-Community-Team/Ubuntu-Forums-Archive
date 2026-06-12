---
title: "How do I access video files on Ubuntu 14.04 from a DVR on a lan?"
date: 2016-04-30
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2016-04-30
Dvr = Humax  HDR-FOX T2. It uses DHCP for accessing remote sources.
Computer with remote source video files: Ubuntu 14.04 gnome ubuntu

 My router's web interface  states the  wired network's IP address is 192.168.1.5

I set the DVR's  network setting in its menu   to IP: 192.168.1.10, network 255.255.255.0, gateway 192.168.1.10, DNS 192.168.1.254

How do I discover the correct DVR network settings because with the ones above,   the router web interface is not showing the  dvr as a device connected to the home network?

---

### Post by T.J. on 2016-04-30
That depends on what ways your DVR communicates on a network.  Does it use a web interface or can it share files with Windows over file-sharing, for example? 

One thing that does look unusual is the gateway setting.  It is usually .1 on a LAN.  You have your DVR as a host and a gateway.  That is probably not going to work.  A gateway is the IP address of the device that connects your LAN to the rest of the world - ie "gateway to the outside".  I'm assuming that is your router.

[https://en.wikipedia.org/wiki/Default_gateway](https://en.wikipedia.org/wiki/Default_gateway)

---

### Post by Robbyx on 2016-05-07
Thank you for the reply. 

I am still unclear how to find the router's address assuming that is the default gateway.

In order to avoid stripping down the network connections I have looked at the wired connection in the computer's network connections and it shows:

IP address   ....1.5
Default root ...1.254
DNS             ...1.254

Is a default root the same as a default gateway?

(In nmap 192.168.1.254  is described as dsldevice.lan)

To see what would happen I changed the default gateway lan setting on the DVR to 192.168.1.254. In the menu setup it reports network connected, but if I try to switch the storage location to the lan it reports it is connecting, the connecting does not stop, and it does not actually show me the HD of my computer.

This is the nmap after changing the setup:

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2016-05-07 22:17 BST
Nmap scan report for Unknown (192.168.1.2)
Host is up (0.040s latency).
Nmap scan report for robins-desktop (192.168.1.5)
Host is up (0.00015s latency).
Nmap scan report for dsldevice.lan (192.168.1.254)
Host is up (0.0063s latency).

Is it possible that my additional router is causing the problem? I have a router/ modem supplied by my ISP, and I bought another router to add extra sockets. the DVR goes into the extra router which is connected by cable to the modem router. As nmap is not showing the TV or the DVR lan connection I wonder if the default gateway is wrong and that I have to find the address for the extra router not the ISP router. If so how do I do it?

 


R

---

### Post by Robbyx on 2016-05-09
In order to make it easier to guide me here is the output from route -n
see [http://www.cyberciti.biz/faq/how-to-find-out-default-gateway-in-ubuntu/](http://www.cyberciti.biz/faq/how-to-find-out-default-gateway-in-ubuntu/)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


Am I right in assuming that the gateway address  is  192.168.1.254 ?

---

### Post by DuckHook on 2016-05-09
You have certainly made it needlessly complicated and difficult for yourself. Let's try to unravel a bit of this knot:

1. You need to find the IP address of your first router (the one supplied by your ISP). I'm assuming that you never changed it from its default. Most commercial routers use a default of 192.168.1.1 but this is not always the case. Read your documentation to find it. It's the address that you point your browser to in order to bring up your router settings. *Do not change any settings on this router*. It is your key to reaching the outside world and should not be messed with unless you really, really know what you are doing.

2. You need to find the IP address of your second router (the one you added). Again, most commercial ones are defaulted to 192.168.1.1. Read the documentation that came with your second router. It is unusual to have two routers on a simple home network unless you know what you are doing. The better solution is to use a switch or a hub which lacks the router server software.

3. The two routers are likely conflicting with each other since they would likely both share the same IP and also both have dhcp active. So, you must:

[LIST=A]
[*]Change the IP address on your second router to its own unique non-conflicting one (say, 192.168.1.2).
[*]Disable DHCP on your second router so that it no longer acts as a conflicting DHCP server. *You can only have one dhcp server on any given network*.
[*]Disable WIFI on second router.
[*]To avoid interference from the first router, you will have to do these things with the second router disconnected from the rest of the network and connected straight into your computer.
[/LIST]
4. Some DVRs have the bad habit of acting as their own dhcp server. I have one of those and they are stupid and unbelievably irritating. You will have to read your user's manual to see if dhcp exists and how it can be disabled. Again, *it must be disabled*. Your user's manual will also tell you what your unit's factory-set static IP is. This IP address *cannot* be the one on your first or second router. *Every IP on a network must be unique* so set it to, say, 192.168.1.3 but whatever you choose, it must be of the form: 192.168.1.n where n is a unique number from 1 to 254. Just like your second router, you may have to disconnect your DVR from the network and directly up to your computer to make these changes.

You are beginning to see the pattern. Printer can be 192.168.1.4 etc.

All devices must have subnet mask: 255.255.255.0
All devices, *but not the first router*, must have gateway: 192.168.1.1 (i.e. the IP of your first router)
All devices should have local DNS of 192.168.1.1

**SPECIAL OPTION**

At risk of further confusion, it is actually easier if you set your second router, your DVR, and whatever other peripherals you have (like printers) to dynamic IP addressing and not give them a static IP address at all. Then you can assign their MAC addresses to a static IP inside the first router, and for all intents and purposes, they will always have an unchanging IP address anyway. This makes your life easier because you can manage most of your network topography from one place, your first router. If you choose this option, you don't need to set any of your peripherals' IP addresses, or any of the other settings above. Just make sure they are set to dynamic IP addressing and they will receive their configurations automatically from your master router.

After all of the above has been done, you should be able to point your computers to the IP address of your DVR (using our example above, that would be 192.168.1.3) and they should be able to see it. As one final note: it is actually better to refer to your DVR by its hostname wherever possible. That way, if its IP address should change, you won't have to change your references in your other machines.

---

### Post by Robbyx on 2016-05-26
Thank you for your very helpful response. I am still struggling but this time with the firewall blocking communications between the computer and the dvr. Would you mind looking at my question at [http://bit.ly/1TEDWJX](http://bit.ly/1TEDWJX)

PS
I have the interface working between the two provided the Gufw is not operational. So i need to make a rule to allow communication between the devices.

---

