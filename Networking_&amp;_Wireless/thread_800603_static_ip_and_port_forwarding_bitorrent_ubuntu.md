---
title: "static ip and port forwarding bitorrent ubuntu"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Truthseeker on 2008-05-20
I've been trying to do a port forward for my torrents in ubuntu, specifically using utorrent, transmission, and deluge, but to no success. I have no idea how to make a static ip which I take it is necessary for a port forward,  [www.portforward.com](www.portforward.com)  does not have instructions for ubuntu, its instructions for win xp aren't helpful, as far as I know.  I've searched the internet I realized that this is a big problem with many, but I still couldn't find a solution. Many weren't even speaking of a static ip.    I have a wired single Speedtouch modem, connected to a wireless Belkin G router.

---

### Post by helgman on 2008-05-20
Are you trying to set a static IP? (Here is [one guide (GUI)](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html) and here is [another guide (CLI)](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html).)

Do they help?

Regards,
Helgman

---

### Post by Truthseeker on 2008-05-20
Well I need a static IP to do a portforward right?



For the GUI tutorial, one step says _"If you want to configure the Static ipaddress you need to select drop down box under &#8220;Configuration&#8221; select static ip address and you need to make sure &#8220;Enable this connection&#8221; tick box is checked"_

but my Network window says "enable roaming mode"   when I unselect it I can then edit it to be static IP and type in the addresses, then when I select "enable roaming mode" the edited fields stay edited but it goes back to a default connection.   When I leave it unselected my internet cuts off


another step says _"now you click on &#8220;General&#8221; tab here you can enter your hostname,domain name"_

what is my host name and domain name exactly?


I don't think I need to further configure my DNS and Hosts settings as its outlined because I'm always using this computer for the same purpose.

---

### Post by helgman on 2008-05-20
OK ... well, you sort of need a static IP address, yes, or at least you need to have the same IP address every time you are connected to your home network.

If you have access to the DHCP server then you might have the option to tell it to always give the same address to your computer, that way you don't have to reconfigure the network settings on the computer and still get the same address and yes, if you want to forward a port you have to specify to what IP address.

Now, I'm no master at the Network Manager but roaming mode, I guess, is used to let the manager adapt to whatever network you connect to. So you shouldn't use that if you are using static IP (I might be wrong here).

What you need to set is IP address, subnet mask, default gateway and DNS server. Host name (name of computer) and domain name (name of "network") are just bonuses, you shouldn't have any need for them.

Let me know if there is anything you need to help with finding.

Helgman

---

### Post by Truthseeker on 2008-05-20
> **helgman said:**
> If you have access to the DHCP server then you might have the option to tell it to always give the same address to your computer, that way you don't have to reconfigure the network settings on the computer and still get the same address and yes, if you want to forward a port you have to specify to what IP address.


What you need to set is IP address, subnet mask, default gateway and DNS server.
and how do I do this?

---

### Post by superprash2003 on 2008-05-20
system->administration->network

---

### Post by Truthseeker on 2008-05-21
yes I did try that,   as my previous post says, my Network window says "enable roaming mode" when I unselect it I can then edit it to be static IP and type in the addresses, then when I select "enable roaming mode" the edited fields stay edited but it goes back to a default connection. When I leave it unselected my internet cuts off

---

### Post by helgman on 2008-05-21
If you want your DHCP server to always offer the same address you have to know where your DHCP server is ... it's either your Belkin or your Speedtouch I guess.

Post the product name and model number of both of them and then a quick description of how your network is set up (what IP addresses they have etc).

How are you cut of? Can you ping any of the devices on your LAN?

Regards,
Helgman

---

### Post by Truthseeker on 2008-05-21
speedtouch 516, regular, one ethernet dsl modem

belkin wireless g router, model F5D7230-4


 IP address	192.168.2.1
 
Subnet mask	255.255.255.0
 Subnet mask	255.255.255.0
   Wan IP	206.248.159.105
   Default gateway	206.248.154.102
   DNS Address	206.248.154.22


how do I ping devices on my LAN?

---

### Post by helgman on 2008-05-22
If the above IP address etc is from your Belkin then I guess that's the device you should use for port forward and then it's the Belkin that is working as you DHCP server. Unfortunately, from what I can see, you can't set it do always serve the same IP address to a specific MAC address (but I'd ask around with someone who knows the Belkin products just to make sure). 

> **Truthseeker said:**
> how do I ping devices on my LAN?

Open a terminal and write *ping <IP address>* so to ping your Belkin you write *ping 192.168.2.1* and hit enter.

Regards,
Helgman

---

### Post by Truthseeker on 2008-05-22
where do you see that I can't set a static IP for my router?   What is a "MAC" address?


I did the ping thing, and it just keeps going with this:

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.383 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.368 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.379 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=0.365 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=0.358 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=0.366 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=0.361 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=0.381 ms

---

### Post by helgman on 2008-05-23
> **Truthseeker said:**
> where do you see that I can't set a static IP for my router?

I skimmed through the manual (found at the Belkin homepage) and I found nothing indicating that it can be done. I won't get angry if you prove me wrong ... ;-)

To be clear: I didn't find any instruction for setting the DHCP server in the Belkin to hand out specific IP addresses to specific MAC addresses ...

> What is a "MAC" address?

Good question. It's a Media Access Control address, a hardware address of a network interface. It's used (among other things) for Ethernet communication and it's a big deal in computer communication. You will find more information [here](http://en.wikipedia.org/wiki/MAC_address). The MAC address is a way to "identify" a specific network adapter and it "should" be unique among all network cards.

If you want a DHCP server to hand a specific IP address to a specific computer, you tell the DHCP server that "when a request comes from MAC address XX:XX:XX:XX:XX:XX then give it IP address X.X.X.X. 

> I did the ping thing, and it just keeps going with this:

Yepp, it just keeps going until you tell it to stop. You can give it specific instruction about how many times it should send out ECHO REQUESTs etc, try **man ping** for more information.

> PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.383 ms

This indicates a success, you get a seq(uence) number and the time it took to complete the ECHO REQUEST / ECHO REPLY (I think). A successful ping to 192.168.2.1 when you are connected at home indicates that you are connected to your local network.

Regards,
Helgman

---

### Post by Truthseeker on 2008-05-23
so basically you're saying I can't setup a static IP address because Belkin routers don't support it????? That seems a bit stretching it isn't it?

---

### Post by helgman on 2008-05-24
> **Truthseeker said:**
> so basically you're saying I can't setup a static IP address because Belkin routers don't support it????? That seems a bit stretching it isn't it?

No, what I'm saying is that your can't have you computer set to dynamic and have your router hand you the same IP address every time.

So, you can't use roaming mode, you have to set a static IP address directly on your computer.

> yes I did try that, as my previous post says, my Network window says "enable roaming mode" when I unselect it I can then edit it to be static IP and type in the addresses, then when I select "enable roaming mode" the edited fields stay edited but it goes back to a default connection. When I leave it unselected my internet cuts off

This is why we investigated the Belkin. Just don't select "Enable roaming mode" and you should be fine.

As for you connection cuts of ... you might have missed something. Did you set your router (192.168.2.1 if I remember correctly) as your default gateway?

Regards,
Helgman

---

### Post by Truthseeker on 2008-06-03
I put in the IP address of my router and not my modem right?


Are you referring to the Gateway address? The last field to be filled in the connection settings window?  For that I also put 192.168.2.1  my router IP address.

My configuration is set to "static IP address"

but after doing this and with the "enable roaming mode" unselected my internet doesn't work

---

### Post by helgman on 2008-06-04
> **Truthseeker said:**
> My configuration is set to "static IP address"

but after doing this and with the "enable roaming mode" unselected my internet doesn't work

OK ... do like this then:

1) Enable roaming mode and when you are sure you are connected to the Internet do the following (and post the output here):

[INDENT]a) ifconfig
b) route -n
c) cat /etc/resolv.conf[/INDENT]

2) Make the static settings once again and then run the commands one more time, what is the difference in the output?

3) While having the static settings ... try to **ping 66.249.93.99**.

And then we'll take it from there, I hope.

Regards,
Helgman

---

### Post by Truthseeker on 2008-06-05
how do I do step 1?    Sorry, I'm a ubuntu and linux noob

---

### Post by helgman on 2008-06-05
Open a terminal, *Applications -> Accessories -> Terminal*, then type the command and press *Enter*. Select the text that the command generates, right click on it and select copy. Past it in your next post.

*I'm gonna be on the road about a week and I'm not sure how often I'll be able to read the forum but I'll try as often as I can.*

Regards,
Helgman

---

### Post by Truthseeker on 2008-06-07
_Step 1 a)_

eth0      Link encap:Ethernet  HWaddr 00:13:20:9d:fc:34  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe9d:fc34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59269589 (56.5 MB)  TX bytes:152103605 (145.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56100 (54.7 KB)  TX bytes:56100 (54.7 KB)


_1 b)_    

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0


_1 c)_

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4684
#
### END INFO

search Belkin


nameserver 192.168.2.1


_2 a)_

eth0      Link encap:Ethernet  HWaddr 00:13:20:9d:fc:34  
          inet6 addr: fe80::213:20ff:fe9d:fc34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59750808 (56.9 MB)  TX bytes:163464163 (155.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56784 (55.4 KB)  TX bytes:56784 (55.4 KB)


_2  b)_

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


_2  c)_

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4684
#
### END INFO

search Belkin


nameserver 192.168.2.1


_3_

connect: Network is unreachable

---

### Post by helgman on 2008-06-08
So ... when you set things up in the Network Manager and then close it you get the output in Step 2?

If you compare the two you see that the IP address in not set in Step 2a and then you can't have a default route (you don't have any route since you don't have an address):

> **Truthseeker said:**
> _Step 1 a)_

eth0      Link encap:Ethernet  HWaddr 00:13:20:9d:fc:34  
**          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0**
          inet6 addr: fe80::213:20ff:fe9d:fc34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59269589 (56.5 MB)  TX bytes:152103605 (145.0 MB)

_1 b)_    

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
**0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0**

[...]

_2 a)_

eth0      Link encap:Ethernet  HWaddr 00:13:20:9d:fc:34  
          inet6 addr: fe80::213:20ff:fe9d:fc34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59750808 (56.9 MB)  TX bytes:163464163 (155.8 MB)

_2  b)_

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

I've got to try this out on a computer running Ubuntu to see if I can repeat your problem. Be back as soon as possible.

Regards,
Helgman

---

### Post by Truthseeker on 2008-06-11
thanks alot for the help you've given me so far and the time you've spent.  


I'll again confirm what I inputted in the network settings window just to make sure we're both on the same track.

-enable roaming mode is unselected

-configuration is set to  "Static IP address"

-the "IP address" field is filled in with my router(?) ip  192.168.2.1

-the "Subnet mask" field is filled with what my router webpage (192.168.2.1) shows it as    255.255.255.0

-the "gateway address" is filled with what my router webpage calls as "default gateway"   206.248.154.101

---

### Post by helgman on 2008-06-12
> **Truthseeker said:**
> thanks alot for the help you've given me so far and the time you've spent.

No problem. I finally have a good connection for an hour or two so let's see what we can do.

> I'll again confirm what I inputted in the network settings window just to make sure we're both on the same track.

I went through the settings and if I interpret them correctly we might have found the problem.

If you connect to the Internet through the router then your computer should not have the same **IP address** as the router. It should be on the same [subnet](http://en.wikipedia.org/wiki/Subnetwork) as the router but it should not have the same address. If you don't have any other computers on the LAN you can pick any address between 192.168.2.2 and 192.168.2.254 but if there are other machines connected (or printers etc) then you should try and find an IP address that is outside of the scope that the DHCP server (in the router) use (consult the manual if you are unsure). The **subnet mask** looks fine.

As for **gateway address** you should put the router address, that is 192.168.2.1. This is the address the computer uses to reach the Internet in this case, that is, the router. ([Wikipedia](http://en.wikipedia.org/wiki/Default_gateway) has an article about the "Default gateway", it's rather basic but it might be worth the read non the less.)

So, try changing the settings as explained above and see what happens, and don't hesitate to ask if anything is unclear.

Regards,
Helgman

---

### Post by Truthseeker on 2008-06-16
hmm, you know I automatically assumed that what my router webpage says as "IP address" is my computer's IP address. Where do I find my actual computer's IP address?

I have another computer that uses the wireless router.  The router's manual will have the DHCP server's range of IP's that I need to stay away from?

---

### Post by helgman on 2008-06-16
> **Truthseeker said:**
> hmm, you know I automatically assumed that what my router webpage says as "IP address" is my computer's IP address. Where do I find my actual computer's IP address?

You don't. Since you want to set it to a static IP address it's your choice what address to use (see below).

> I have another computer that uses the wireless router.  The router's manual will have the DHCP server's range of IP's that I need to stay away from?

The manual might have these settings, but the router will. If you are unsure about how to find them, just consult the manual for how to set up the DHCP server and you'll find the answer there (in the router configuration). If the range is from x.x.x.2 to x.x.x.254 just change the range (x.x.x.50 to x.x.x.100 might be enough) and put the IP of your computer outside that scope (maybe something like x.x.x.10).

Regards,
Helgman

---

### Post by Truthseeker on 2008-06-18
okay, so right now what I need to change in the network window fields is first the IP Address which needs to be outside the range of the DHCP server router right?

Previously you said that the gateway address field should have my router address (192.168.2.1) if I'm connecting to the internet through my router.  I'm connecting to the internet through my router if the ethernet cable goes directly from the PC to the router right?

---

### Post by helgman on 2008-06-19
> **Truthseeker said:**
> okay, so right now what I need to change in the network window fields is first the IP Address which needs to be outside the range of the DHCP server router right?

Yes, outside of the DHCP scope (but in the same subnet). So, to make this clear:

Your router has IP address 192.168.2.1.
The router has a DHCP scope of for example 192.168.2.50 - 192.168.2.254.

Then you give your computer an address between 192.168.2.2 and 192.168.2.49.

> Previously you said that the gateway address field should have my router address (192.168.2.1) if I'm connecting to the internet through my router.  I'm connecting to the internet through my router if the ethernet cable goes directly from the PC to the router right?

Correct.

Regards,
Helgman

---

