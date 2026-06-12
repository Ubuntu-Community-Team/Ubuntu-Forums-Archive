---
title: "Ubuntu disconnecting from VLANS"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by elperrillo on 2008-07-31
This is for all network GURUS...

I am having a real problem with a new UBUNTU (hardy) server in my company. all of a sudden it is not being seen by other vlans... It does not even let me ping addresses on other vlans. 

Here is what I know...

1) It is not a network problem, all my windows servers work fine with no special configuration. I even have a Fedora server wich works fine.

2) When I reboot my UBUNTU server it works for a while but then all of a sudden it does not see the VLANS on my network anymore. I use to reboot it once a day, now it is constant... it works for half an hour or so and then thats it.


Does anybody have any idea of what might be happening?

---

### Post by casevh on 2008-07-31
Are you using a locally assigned IP address or an address provided by a DHCP server? 

When the problem occurs, can you ping other computers on your subnet?

When the problem occurs, can you ping the default gateway for your subnet (VLAN)?

casevh

---

### Post by elperrillo on 2008-07-31
Thanks for your response.

1) My IP is static

2) I have a Fedora server with the EXACT same network configuration, and it runs just perfect (it has been running perfect for years without a single glitch, I had to actually disconnect my UBUNTU server and go back to this old server which is running on a PIII machine!!!).

3) Both servers do the exact same thing and they both have two network cards connected to two different networks (they are proxy servers)

4) If I go to the web using fedora, I get out to the web using my workplace's network, if I get out to the web using UBUNTU is uses the other network.

5) Basically UBUNTU has problens with my internal network, I can ping the server that redirects computers to the vlans from ubuntu. I can ping anything on my local domain exept the vlans. I do not get any reply when I ping anything on a vlan, it just stays there with no response, not even "destination unreachable"... nothing... blank screen. (My Fedora does not give my a reply from the actual machines on the vlans but it gives me a reply from the redirection server when I ping something on a vlan.)
 


how can you explain this weird behavior???

---

### Post by casevh on 2008-07-31
Have you compared the routing tables between the two systems?

Use the command "netstat -rn".

casevh

---

### Post by elperrillo on 2008-07-31
Yeah, they actually look different even though their IP configuration is the same, here they are, (I've modified the ips for security reasons, but keeping the same structure)

Fedora

Kernel IP routing table
Destination     Gateway          Genmask         Flags   MSS Window  irtt Iface
49.30.133.9     0.0.0.0          255.255.255.240 U         0 0          0 eth0
192.168.0.0     0.0.0.0          255.255.0.0     U         0 0          0 eth1
50.254.0.0      0.0.0.0          255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.254.254  0.0.0.0         UG        0 0          0 eth1


Ubuntu

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
49.30.133.9     0.0.0.0         255.255.255.240 U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
50.254.0.0      0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.254.254 0.0.0.0         UG        0 0          0 eth1
0.0.0.0         49.30.133.10    0.0.0.0         UG        0 0          0 eth0

Its a litle hard to see because the Furun removes the spaces, I wish it would let me use a table.

---

### Post by casevh on 2008-07-31
You have two default routes and I bet the system is getting confused as to which one to use. I would try deleting the default route going to 49.30.133.10.

If that doesn't, I would normally use wireshark to capture the packets leaving both interfaces and check if the pings, etc. are being sent out the correct interface.

casevh

---

### Post by elperrillo on 2008-07-31
"getting confused" that is exactly how I would describe the problem. I am going to try that, I actually do not know how to delete those routes, if you know it off the top your head please post it, if not don't worry I will find out. I wonder how that got in there, would that be a "persistent route"? I have not added any routes myself. 

Thanks so much for your help, I really really really appreciate it.

---

### Post by casevh on 2008-07-31
Off the top of my head, the command to do it on the fly is

route del default gw 49.30.133.10 eth0

casevh

---

### Post by elperrillo on 2008-07-31
That command worked however, once I reboot it I got it again, but that is not all, now one of the lines changed... take a look

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
49.30.133.9   0.0.0.0         255.255.255.240 U         0 0          0 eth0
192.168.0.0        0.0.0.0         255.255.0.0     U         0 0          0 eth1
50.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.254.254     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         49.30.133.10   0.0.0.0         UG        0 0          0 eth0

If you notice the line that has 50.254.0.0 is now assigned to eth0 instead of eth1!! This is totally crazy! Is there any way of making these changes permanent, maybe changing the metric of one or the cards or something?

---

### Post by casevh on 2008-07-31
Now it's starting to get interesting.

Is there anything in /etc/network/interfaces that is creating those routes?

casevh

---

### Post by elperrillo on 2008-07-31
Nope, I thought of that and I checked that file but it looks normal, what I see there is the same as in the regular UBUNTU network config. this is really strange.

---

### Post by casevh on 2008-08-01
Hmm.

Based on the output of netstat, it doesn't look like you are running any routing protocols. If there are no static routes being entered via a script, then we need to look at something outside the server.

If you power up the Ubuntu server with the two ethernet ports connected to separate, standalone dumb switches, do you still get the strange entries in the routing tables?

If the answer to the about is "no", you may be receiving ICMP redirect messages from the network. I would disable ICMP redirects on any "secure" server. See the following link for details.

[http://www.itsyourip.com/Security/how-to-disable-icmp-redirects-in-linux-for-security-redhatdebianubuntususe-tested/](http://www.itsyourip.com/Security/how-to-disable-icmp-redirects-in-linux-for-security-redhatdebianubuntususe-tested/)

casevh

---

### Post by elperrillo on 2008-08-01
Hi I am not at work today and I can't try it. I actually have access to the server though VPN and VNC however if I reboot the server I will loose connection though VNC and I will never be able to log back in again, unless I am physically there.

However I was reading the article and I have a question about the following paragraph...

"If ICMP Redirects are not used in the network for route updates and if the server is not acting as a Router or a Gateway (ICMP Redirect send only) then ICMP Redirect send and accepts should be disabled on the server."

Wouldn't this change affect this server since it is a proxy server, linking two different networks?

---

### Post by casevh on 2008-08-01
There are several concepts involved. When the article mentions "route updates", they are talking about the messages one router sends to another router to identify which networks are networks are reachable and what the metric (cost) is. If you were running gated or quagga or zebra on your server, it could also listen to those updates and determine where networks were located and where to send packets destined for those networks. Networks learned via a routing protocol are tagged with a "D" in the output of "netstat -rn". I didn't see any dynamically learned routes.

ICMP redirect messages can be used to change the routing tables for systems that are not using a routing protocol. For example, assume you have PC on a network subnet. There are two routers on that subnet - one that connects to the rest of the company and another that connects to the Internet. Typically, the PC only has one default gateway - the one that connects to the rest of the network. If the PC trys to send a packet to the Internet, the "company" router will send the packet to the "Internet" router but it can also send an ICMP redirect message to the PC and to redirect traffic for that network to a different destination address, in this case, the "Internet" router.

ICMP redirect messages can also be used to intercept traffic and perform DOS attacks. I normally design networks so ICMP redirects are not needed.

In your environment, the server's routing table should be static - it always needs to send traffic the same way. Since the destination gateway address (or next-hop) should not change, your server shouldn't be listening to ICMP redirects or routing updates. But it will still act as a proxy.

Does this help?

casevh

---

### Post by elperrillo on 2008-08-04
Hi:

I got back to work this morning and tried what you suggested, I followed the article and disabled ICMP redirects, pasting the lines on the startup file listed in the article to disable ICMP redirects "globally". I flushed the routing table and then rebooted and ran "netstat -rn" and nothing, I got the same exact weird entries.

Then I flushed the table again and shut down the server and connected both network cards to a single switch which I had laying arround. and that gave me the following output when I ran "netstat -rn"...

49.30.133.9  0.0.0.0          255.255.255.240 U         0 0          0 eth0
192.168.0.0  0.0.0.0          255.255.0.0     U         0 0          0 eth1
50.254.0.0   0.0.0.0          255.255.0.0     U         0 0          0 eth1
0.0.0.0      192.168.254.254  0.0.0.0         UG        0 0          0 eth1
0.0.0.0      49.30.133.10     0.0.0.0         UG        0 0          0 eth0

Notice that the only change is that the third line changed back from eth0 to eth1.

I removed it from that switch and placed it back the way it originally is, on it original switched and that third line changed back to eth0.

I waited a while and ran netstat -rn again and all of a sudden now the third line is back to eth1 without me doing absolutely anything!!!!!!

This is totally crazy!!! What do you think now?

---

### Post by casevh on 2008-08-05
I'm running our of ideas but I have one more. In /etc/network/interfaces, I assume you both IP addresses listed similar to below:

iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

The gateway entry creates the default route. Only the interface going towards the internet should specify a default gateway.

Does this help?

casevh

---

### Post by elperrillo on 2008-08-06
Hi, I did have two gateways for the two different network cards, so I removed the one I did not need and when I ran "netstat -rn" everything looked exactly like in my FEDORA server, However once I rebooted This is what happened....

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
49.30.133.9    0.0.0.0          255.255.255.240 U         0 0          0 eth0
192.168.0.0    0.0.0.0          255.255.0.0     U         0 0          0 eth1
50.254.0.0     0.0.0.0          255.255.0.0     U         0 0          0 eth1
0.0.0.0        192.168.254.254  0.0.0.0         UG        0 0          0 eth1

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
49.30.133.9   0.0.0.0           255.255.255.240 U         0 0          0 eth0
192.168.0.0   0.0.0.0           255.255.0.0     U         0 0          0 eth1
50.254.0.0    0.0.0.0           255.255.0.0     U         0 0          0 eth0
0.0.0.0       192.168.254.254   0.0.0.0         UG        0 0          0 eth1

Notice how the third line got changed again from eth1 to eth0...

Here is my "interfaces" file, maybe you can spot if I have anything wrong in there. One thing I noticed is that my DNSs belong to the network of the card that does not have a gateway now, I do not know if squid will work without those DNSs I doubt it.... Here it is, that all I have there:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 49.30.133.10
netmask 255.255.255.240

auto eth1
iface eth1 inet static
address 192.168.1.112
netmask 255.255.0.0
gateway 192.168.254.254

---

### Post by phranqburke on 2008-09-26
There is a bug that causes the system to reorder interfaces.  Read about it at /usr/share/doc/ifupdown/examples/network-interfaces.gz.  A workaround is referenced by the document.

Frank

---

### Post by elperrillo on 2009-02-05
Hi, does anybody know if this bug has been resolved with 8.10? (when I started this thread I was using 8.04, I just upgraded to 8.10) I really would not like to go back to Fedora.

---

### Post by frobroj on 2009-08-12
I am a bit curious as well. 

Currently I have bypassed the same problem by setting all vlan interfaces as statics and making sure to leave out the gateway x.x.x.x command. (/etc/network/interfaces)

It would be nice if there was a "gateway override/block" command for dhcped ints. Some of the lans I am on I would rather just pull dhcp. I tried the "up route del/add" command to try to remove and put in the route I wanted for that int but it didnt work well for me and it seemed pretty cludgy so I went with statics.

Thanks for letting me add my two cents to the conversation.

---

