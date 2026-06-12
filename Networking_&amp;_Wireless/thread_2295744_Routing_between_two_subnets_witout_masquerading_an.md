---
title: "Routing between two subnets witout masquerading and withoud configuring hosts"
date: 2015-09-21
forum: Networking &amp; Wireless
---

### Post by bbruecker on 2015-09-21
What I wanted to do is this:

```

Internet <---> Router-from-ISP         Ubuntu-Router
               192.168.0.1     <-----> 192.168.0.3 (eth0)
               Web-Server         |    192.168.1.1 (eth1)  <---> Clients
               192.168.0.2     <---                              192.168.1.100-192.168.1.100.150
```
There are lot of descriptions for this, on which the Ubuntu-Router (Server 14.04) would mask the hosts from each subnet. This is not what I wanted to do, because all clients need to access the Web-Server, and some the Router-from-ISP as well. I found one posts which give me hope that this could work ([http://ubuntuforums.org/showthread.php?t=1905048](http://ubuntuforums.org/showthread.php?t=1905048)). But in my case I have changing Clients, which I don't won't/can't configure. Is there a way without adding a route on each of the clients, for accessing the Web-Server (192.168.0.2) or Router from the 192.168.1.x-subnet? 

If you ask your self, why the hell I'm doing that (one subnet would be more easy): I need some IP-filters, which I would like configure later using ufw or ip-tables (thats not part of the topic right now). the router from my ISP doesn't offer such functionalities.

---

### Post by The Cog on 2015-09-21
Do your clients need internet access? If so...

Your clients absolutely have to have a route configured. A single default route will do, pointing them to 192.168.1.1. 
A default route is one that says "Send all your off-net packets to *this *address" and points to a router known as the default gateway.
I would expect that this default route would be issued by the DHCP server that also autimatically allocates unique IP addresses to new PCs that are added to this LAN.
I've not configured a DHCP server other than in a home router (which always announces itself as the default gateway), but I imagine they can all be configured to announce a specified default route.

You can configure masquerading on your Ubuntu router eth0 with this command. Masquerading is required for your clients to access the internet, and will remove the need for the web server and ISP router to know a route to 192.168.1.*.:
```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

--------------------
If your clients don't need internet access then you can set up some dummy IP addresses on your router as proxy addresses for the web server and ISP router. This way, the clients don't need to know any routes at all because the servers will appear to be on the local 192.168.1 network. This will work as long as the servers don't issue links between pages using URLs with their real addresses in them.

These commands should do the trick (I have chosen addresses 192.168.1.101 and 192.168.0.102 as the proxy addresses, you will have to replace these with addresses that you know nothing else will try to use):
```
sudo ifconfig eth0 192.168.1.101 netmask 255.255.255.0
sudo ifconfig eth0 192.168.1.102 netmask 255.255.255.0
iptables -t nat -A PREROUTING -i eth1 -d 192.168.1.101 -j DNAT --to-destination 192.168.0.1
iptables -t nat -A PREROUTING -i eth1 -d 192.168.1.102 -j DNAT --to-destination 192.168.0.2
```

---

### Post by helgman on 2015-09-21
> **bbruecker said:**
> There are lot of descriptions for this, on which the Ubuntu-Router (Server 14.04) would mask the hosts from each subnet. This is not what I wanted to do, because all clients need to access the Web-Server, and some the Router-from-ISP as well.

Both the ISP-router and the web-server needs to be aware of network 192.168.1.0/24. This is the main problem that is solved through masking the hosts on the 192.168.1.0 network in the Ubuntu-router (as explained by The Cog). If you can make a route on the ISP-router telling it to send all packages for 192.168.1.0/24 to 192.168.0.3 then you won't need any masquerading to get it to work. The same goes for the web-server.

When it comes to the clients on the 192.168.1.0/24 network you should follow the directions given by The Cog regarding "default gateway" configuration.

Good luck!
Helgman

---

### Post by bbruecker on 2015-09-23
The Cog, thank you for the detailed explanation!
> **The Cog said:**
> Do your clients need internet access? If so...
Yes, that's my situation. After reading your replay I found some solutions to provide routes for clients by DHCP. So it should work without touching every computer.
But now I'm not able to connect the subnets, and I would appreciate some help.
I tried on the server this command:
```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
And on my client in the 192.168.1.x subnet I tried this:
```
sudo ip route add 192.168.0.0/24 via 192.168.1.1 dev wlan0
```
I still cannot ping internet or any computer within the 192.168.0.x subnet. Maybe I need to configure the server a bit more?
THX!

---

### Post by helgman on 2015-09-23
> **bbruecker said:**
> 
```
sudo ip route add 192.168.0.0/24 via 192.168.1.1 dev wlan0
```
I still cannot ping internet or any computer within the 192.168.0.x subnet. Maybe I need to configure the server a bit more?
THX!

It is strange that you do not get any answers from the 192.168.0.x subnet. Is the masquerade up and running as it should be? (I wish I knew a command for "seeing" this in Linux but I do not at the moment and I have no luck with a quick google and no computer I can test it on.) Does a ping from one of the clients to the server or router "time out" or do you get some other kind of error message?

To get your packets out to the internet you need to add route to  0.0.0.0/0 (or "default"):

```
sudo ip route add default gw 192.168.1.1
```

---

### Post by SeijiSensei on 2015-09-23
I don't see any need for masquerading on Ubuntu-Router.

1)  Make sure IP forwarding is enabled in /etc/sysctl.conf on that machine.  Uncomment the line that reads
```
net.ipv4.ip_forward=1
```
To make that active, you'll need to reboot or issue the command
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

2)  Also on Ubuntu-Router, set its default gateway to 192.168.0.1. Configure its isc-dhcp-server to give out 192.168.1.1 as the clients' default gateway.

3)  On the web server add this route
```
sudo ip route add 192.168.1.0/24 via 192.168.0.3
```
This tells the web server to send traffic for the routed network to Ubuntu-Router rather than its default gateway of 192.168.0.1.

That should be enough to route the networks.  All the machines in 192.168.1.0/24 should be able to reach the Internet.  Their requests will be passed first to Ubuntu-Router and then on to the ISP's router for transmission to the Internet.  All the masquerading happens there.

However, if people on your internal network will be referencing the web server with a domain name like [noparse]www.example.com[/noparse], you might have problems.  Suppose you have a public DNS server that advertises your router's Internet-facing address for the www host.  You might do this if you have port forwarding enabled on the router to send traffic arriving on its port 80 back to the web server at 192.168.0.2.  If so, your local clients, who will get the public IP address when they ask for "www," might have a problem connecting. 

The request will get masqueraded by the ISP's router and have the identical source and target IP address, the public address of the router.  If the router is "smart" enough, it will know to send the traffic back through itself just as if it came from somewhere else on the Internet.  Some routers can do this; others, speaking from experience, cannot.

If you have this kind of DNS problem, you might consider setting up an internal DNS server running on Ubuntu-Router.  You would create a parallel zone file on that machine for your domain, replacing the current A record for "www" with 192.168.0.2.  You'd need to tell isc-dhcp-server to give out Ubuntu-Router's address, 192.168.0.3, for the primary nameserver.  Then when clients request [noparse]www.example.com[/noparse] that name will resolve to 192.168.0.2, and the traffic will remain local.  I run a local nameserver in my office with a unique set of records pointing names like "www" and "mail" to internal addresses and advertising some local names that have no public equivalent.

---

### Post by helgman on 2015-09-23
> **SeijiSensei said:**
> I don't see any need for masquerading on Ubuntu-Router.

No, not if routes are added on the web server AND the internet connected router (since internet connection (or at least access to the ISP-router) is wanted).

---

### Post by bbruecker on 2015-09-23
Well the problem is, I can not add routes to the ISP-Router and the clients from 192.168.1.x subnet need access to the internet. Do I guess correctly that in this case I need masquerading?

---

### Post by helgman on 2015-09-23
> **bbruecker said:**
> Well the problem is, I can not add routes to the ISP-Router and the clients from 192.168.1.x subnet need access to the internet. Do I guess correctly that in this case I need masquerading?

My guess is 'yes' based on my assumption that the iSP-router will hold three routes, one for each directly connected network (one on the ISP-side and one on your side (192.168.0.0/24)) and one "default route" pointing towards the internet. When something comes in that is to be delivered to one of the clients on the 192.168.1.x subnet the ISP-router will consult its routing table, find the only matching route being the "default route" and either send on towards you ISP or drop it since it is to be sent to a "private address" (as specified in RFC 1918) and that really should not be sent to the internet.

But it is easy to try. Set everything up without masquerading but with routes added on clients and the web server and routing on the Ubuntu-router. If the clients can access the web server but not the internet - you need masquerading if internet access is required but you know that the Ubuntu-router is working as it should. If they can access the internet something is wrong with my guessing and assuming and you do not need to mask the client IP addresses which must be considered a win! :-)

(Knowing that the routing works, even if you need masquerading, makes it easier to troubleshoot later since the problem probably is in the masquerading part of the set up if nothing else was changed.)

---

### Post by SeijiSensei on 2015-09-23
> Do I guess correctly that in this case I need masquerading? 
Yes, you do.  Try
```
sudo /sbin/iptables -A POSTROUTING -o eth0 -j SNAT --to 192.168.0.3
```
on Ubuntu-Router.  You probably don't need a return route to 192.168.1.0/24 on the web server or the ISP router if you take this approach. You may still have the DNS issue I raised before.

---

### Post by bbruecker on 2015-09-27
Hi, thank you all so far! I learned a lot!

I tried out some further steps... but its still not working. Well first of all routing seems to work: I can ping from 192.168.1.x subnet the werbserver, not the ISP router, because I can not add route on that device. 

Just in addition: We don't need any DNS names for the webserver from the 192.168.1. subnet -- which I hope will make it a bit easier!

Now I try to deal with iptables for masquerading: I tried this command:
```
sudo /sbin/iptables -A POSTROUTING -o eth0 -j SNAT --to 192.168.0.3
```

Ubuntu replays: "iptables: No chain/target/match by that name." And still clients from 192.168.1.x subnet still cannot ping internet.

I would like to know another thing: I want to use DNSMASQ for DHCP and manipulating some Internet addresses, like facebook. Will the masquerading leave the opportunity to controll this on Ubuntu Router?

---

### Post by bbruecker on 2015-09-28
I opened a new topic ([http://ubuntuforums.org/showthread.php?t=2296727&p=13364086#post13364086](http://ubuntuforums.org/showthread.php?t=2296727&p=13364086#post13364086)), because the main issue, whether to use IPTABLES or routing is sufficient enough discussed here. The cooperation of DNSMAQS and IPTABLES are a bit different.

---

### Post by SeijiSensei on 2015-09-28
> **bbruecker said:**
> Now I try to deal with iptables for masquerading: I tried this command:
```
sudo /sbin/iptables -A POSTROUTING -o eth0 -j SNAT --to 192.168.0.3
```

Sorry, I forgot the required "-t nat" parameter.  The POSTROUTING target lives in the NAT table.  So the command should read:
```
sudo /sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.0.3
```

---

### Post by bbruecker on 2015-09-29
Thank you SeijiSensei, 
well I was now able to put the command, but its still not working. I still can ping the webserver form the 192.168.1.x subnet, but not the internet (destination host unreachable). I found a way using masquerading by myself described in [http://ubuntuforums.org/showthread.php?t=2296727](http://ubuntuforums.org/showthread.php?t=2296727), but I'm not very happy with that, because the dns server on my ubuntu router is somehow not used. Maybe you can find a mistake in my construction/attempts?

---

