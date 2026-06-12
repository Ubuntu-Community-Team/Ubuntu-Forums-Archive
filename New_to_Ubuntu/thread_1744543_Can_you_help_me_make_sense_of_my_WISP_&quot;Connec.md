---
title: "Can you help me make sense of my WISP &quot;Connection Information&quot;?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by rocksockdoc on 2011-04-30
While wirelessly connected to my WISP provider's antenna directly to my PC while on my property (without the home router in between), when I right click on the "Network Manager"  four-bars icon, and select "Connection Information", what is the significance of the fields displayed?

**Here is what I get from Ubuntu 10.04 Connection Information "Active Network Connections":**

[LIST]
[*]IP Address = 192.168.4.47 <=== this is the laptop's wlan0 IP address assigned by the WISP on the fly
[*]**[COLOR=Black]Broadcast Address = 192.168.4.255[COLOR=DarkRed] <=== what is this?[/COLOR][/COLOR]**
[*]Subnet Mask = 255.255.255.0 <=== AND'ed with 11111111 11111111 11111111 00000000
[*]Default Route = 192.168.4.1 <=== is this normal for the default route to be this?
[*]Primary DNS = 192.168.4.1 <=== what good is setting this to the default route?
[*]Secondary DNS = 8.8.8.8 <=== this is the DNS server that is actually used, I think
[/LIST]
I know I don't understand the "Broadcast Address" (and maybe even the "Default Route").

Can you help me understand what these fields are telling me specifically?

---

### Post by rocksockdoc on 2011-04-30
> **rocksockdoc said:**
> 
[LIST]
[*]**[COLOR=Black]Broadcast Address = 192.168.4.255[COLOR=DarkRed] <=== what is this?[/COLOR][/COLOR]**
[/LIST]
BTW, the web definition for "Broadcast Address" helps me not at all to understand how I would 'use' the broadcast address in my day-to-day life.

> **Web definitions**


[LIST]
[*]In  computer networking, a broadcast address is a network address that  allows information to be sent to all nodes on a network, rather than to a  specific network host.
[/LIST]
[COLOR=#551a8b][en.wikipedia.org/wiki/Broadcast_address]("http://www.google.com/url?url=http://en.wikipedia.org/wiki/Broadcast_address&rct=j&sa=X&ei=UDC8TZT1M5GesQP36bTWBQ&ved=0CCoQngkwAA&q=Broadcast+address&usg=AFQjCNGAPIy7obwMPpBhyRHEIUs0l8sHdA")[/COLOR]


[LIST]
[*]Is an IP address which sends the message to all machines on a local subnetwork.
[/LIST]
[COLOR=#551a8b][www.spywareremove.com/glossary/letter-B.html]("http://www.google.com/url?url=http://www.spywareremove.com/glossary/letter-B.html&rct=j&sa=X&ei=UDC8TZT1M5GesQP36bTWBQ&ved=0CCwQngkwAA&q=Broadcast+address&usg=AFQjCNFzx02cuyyYgkIWXnqMd-DqBLMS7Q")[/COLOR]


[LIST]
[*]An  IP address in each subnet is considered to be the broadcast address for  that subnet. It is the highest numerical value in the range of numbers  for the subnet; the broadcast address cannot be assigned as an IP  address to a computer. ...
[/LIST]
[COLOR=#551a8b][www.proprofs.com/mwiki/index.php/Ultimate_Cisco_CCNA_IN&#8230;]("http://www.google.com/url?url=http://www.proprofs.com/mwiki/index.php/Ultimate_Cisco_CCNA_INTRO_Glossary_%26_Acronyms&rct=j&sa=X&ei=UDC8TZT1M5GesQP36bTWBQ&ved=0CC4QngkwAA&q=Broadcast+address&usg=AFQjCNGHksvmUHtYORZiYsgsffI5VkdGAQ")[/COLOR]
From these definitions, I gather that the highest I can make a computer on my home network is 192.168.4.**[COLOR=DarkRed]0[/COLOR]** ... 192.168.4.**[COLOR=DarkRed]1[/COLOR]** ... 192.168.4.**[COLOR=DarkRed]2[/COLOR]** ... [and so on, up to] ... 192.168.4.[COLOR=DarkRed]**254**[/COLOR]  (since 192.168.4.255 is the highest address ).

Is the highest address I can use all that the broadcast address is telling me (of practical use)?

---

### Post by rocksockdoc on 2011-04-30
Given this quote:
> In  computer networking, a broadcast address is a network address that   allows information to be sent to all nodes on a network, rather than to a   specific network host

I guess if I were to send a message to 192.168.4.255, that message would go to all computers on that network (e.g., the message would go to 192.168.4.**[COLOR=DarkRed]0[/COLOR]** ... 192.168.4.**[COLOR=DarkRed]1[/COLOR]** ... 192.168.4.**[COLOR=DarkRed]2[/COLOR]** ... [and so on, up to] ... 192.168.4.[COLOR=DarkRed]**254**[/COLOR]).

But of what practical significance is that 'feature' to me?
[COLOR=DarkRed][B]
Why would I want to send a message to all computers (i.e., to 192.168.4.255)?
[/B][/COLOR]

---

### Post by QLee on 2011-04-30
[QUOTE=rocksockdoc]...
But of what practical significance is that 'feature' to me?[/QUOTE]

It means that your system would receive a "broadcast" message.
[COLOR=DarkRed][/COLOR][QUOTE=rocksockdoc][COLOR=DarkRed][B]Why would I want to send a message to all computers (i.e., to 192.168.4.255)?
[/B][/COLOR][/QUOTE]

Well, very likely "you" would not, however, the other end (the end that controls transmission to the subnet might want to broadcast a message to all nodes on the network.

---

### Post by QLee on 2011-04-30
[QUOTE=rocksockdoc]..., what is the significance of the fields displayed?[/QUOTE]

Since you seemed impaitient with three posts quickly I answered the last one, anticipating further questions if there were any. Maybe you've got all you need now but since I have to leave, here is a bit more about your original questions.

[QUOTE=rocksockdoc]IP Address = 192.168.4.47 <=== this is the laptop's wlan0 IP address assigned by the WISP on the fly[/QUOTE]

Yup, presumably that "WISP" is a wireless broadband "Modem"/router/NAT (gateway) combination and also has a DHCP server to hand out IP addresses on your LAN. Does that seem like an accurate description of what you have your system plugged into because if it isn't what I write below probably won't make sense.

[QUOTE=rocksockdoc]Subnet Mask = 255.255.255.0 <=== AND'ed with 11111111 11111111 11111111 00000000[/QUOTE]

In the beginning you need not concern yourself with the subnet mask, it can be used in more complex networks but in this case it doesn't alter your address.

[QUOTE=rocksockdoc]Default Route = 192.168.4.1 <=== is this normal for the default route to be this?[/QUOTE]

Yes, the x.x.x.1 address in a subnet could be the "gateway" address, the NAT/router address which all the subnet addresses in your subnet route through to get to the Internet. The address that your WISP gateway presents to the computers inside your LAN.

[QUOTE=rocksockdoc]Primary DNS = 192.168.4.1 <=== what good is setting this to the default route?[/QUOTE]

Well, any DNS request has to get to the Internet (to be translated) through the route, that's the address (very likely passed to your system by the gateway when it assigned the IP address through DHCP).

[QUOTE=rocksockdoc]Secondary DNS = 8.8.8.8 <=== this is the DNS server that is actually used, I think
[/QUOTE]
Well, it would fallback to the secondary if the primary failed but that is a google DNS address so you must have put that in yourself.

Darn, my connection dropped twice while trying to edit, now I really won't be here for questions, sorry, I hope you have enough to go on. There are some "keywords" if you choose to search.

If the "WISP" is something different then a whole different explanation might be necessary, do you have any model number or anything for what you are plugging into?

---

### Post by rocksockdoc on 2011-04-30
> **QLee said:**
> here is a bit more about your original questions.

Thank you for any help. I really do appreciate anyone taking the time to help a fellow soul trying to understand things. 

> **QLee said:**
> presumably that "WISP" is a wireless broadband "Modem"/router/NAT (gateway) combination and also has a DHCP server to hand out IP addresses on your LAN. 

I'm not sure. You'd have to tell me. What I know is that I connect to a line-of-sight antenna which gives me my IP address of 192.168.4.47. 

From that, I 'presume" that they have a NAT on their antenna as that's a non routable address. I would have expected something else, especially since when I do a "http://whatismyipaddress", I get a "real" IP address, but I'm told by my WISP that I share that external IP address with many others.

> **QLee said:**
> Does that seem like an accurate description

Since the WISP give me a non-routeable IP address, I have to assume I'm behind one of their 'routers'.


> **QLee said:**
> I... the subnet mask... in this case it doesn't alter your address.

Interesting. 

> **QLee said:**
> that's the address (very likely passed to your system by the gateway when it assigned the IP address through DHCP).

Interesting also.

> **QLee said:**
> Well, it would fallback to the secondary if the primary failed but that is a google DNS address so you must have put that in yourself.

Actually, for privacy reasons, I didn't put the actual secondary because it would identify my ISP (and I didn't think that would matter what it was). The rest are the same numbers though.

> **QLee said:**
> do you have any model number or anything for what you are plugging into?

From my computer, the RJ45 cat5 cable goes to a Senao (NL-2611CB3 PLUS (DELUXE) LONG RANGE WIRELESS MULTI-CLIENT BRIDGE) which then goes to the antenna aimed at the WISP antenna by line of sight.

---

### Post by QLee on 2011-05-01
[QUOTE=rocksockdoc]Thank you for any help. I really do appreciate anyone taking the time to help a fellow soul trying to understand things. [/QUOTE]

Well, that's what we come here for, eh? (most of us) It was clear that you had some knowledge about the issue so had probably done some investigating on your own, it's easier to want to help someone who is trying to help themself.

[QUOTE=rocksockdoc]I'm not sure. You'd have to tell me. What I know is that I connect to a line-of-sight antenna which gives me my IP address of 192.168.4.47. [/QUOTE] 

Never having seen such service I have to guess so I am reluctant to characterise my explanations as absolutely accurate. 

[QUOTE=rocksockdoc]From that, I 'presume" that they have a NAT on their antenna as that's a non routable address. I would have expected something else, especially since when I do a "http://whatismyipaddress", I get a "real" IP address, but I'm told by my WISP that I share that external IP address with many others.[/QUOTE]

Well, there is a NAT somewhere, generally we would expect to find it in the gateway/router. 

[Edit] It's possible that the "antenna" is more than just an antenna, it probably is also a wireless radio that has a built in network card to connect to your bridge (do you use a network cable or a coax antenna cable to connect the antenna to the bridge?). 

I wonder what they meant by "share", perhaps they just meant that your "real" (Internet facing) IP is dynamically assigned (not a static IP) and thus is "shared" (this is the normal situation unless one pays more for a static IP address).


[QUOTE=rocksockdoc]Since the WISP give me a non-routeable IP address, I have to assume I'm behind one of their 'routers'.[/QUOTE]

Very likely that that adress is coming from your bridge, I can speculate about a different topology for the wide area network but I'd sure like to see how they have things configured. 
...

OK, I've had a look at the Senao (NL-2611CB3 BRIDGE)

From the description online, and your further detail, I'd say it sounds like what we are talking about is, at least, similar to a regular broadband gateway.

It has a web interface, so you can find in the documentation that came with it the instructions for accessing the configuration pages. Generally you just need to point your browser at the gateway IP address (but check your documentation, it will also have any necessary password). 

 If this thing is really like a gateway you should be able to select the range of IPs assigned to your LAN, and that would be done on the configuration pages. On the other hand, because I've not seen one of the Senaco bridges, perhaps they set up the x.x.4.x IP range for some reason (not normally one of the defaults on a gateway).

Sorry I can't really be of much help with no knowledge of the equipment involved.


[Edit] What bandwidth do you get for a connection like this, is it metered (pay per GB of data)?

---

### Post by rocksockdoc on 2011-05-01
> **QLee said:**
> Never having seen such service I have to guess

I understand. I really do. I think 'my' particular ISP has a weird setup. I knew nothing of all this until I had to replace the equipment. 

What I 'think' they have is they have all my neighbors and me on the same 'subnet' (I hope I used that word correctly). 

For example, I can eliminate all variables if I change the MAC address of my wireless card on my laptop to the MAC registered to my WISP. That way you can help explain to me what it is that I actually have (and which I'm trying to fix).

For example, let's assume DE:AD:BE:EF:CA:FE is the MAC address registered as mine for my WISP connection. If I place my laptop (with its puny 1dBi antenna and anemic 50mW wlan0 radio) in a window facing the WISP antenna 1,000 feet away, I can actually (sort of) connect. But I get their router (MicroTik brand) screen asking me to log into their router, which, of course, I can't. 

If I then simply change my Ubuntu PC's wlan0 MAC address to that which the WISP expects, I 'can' connect (and, in fact, I 'am' connected right now in this very manner).
```

$ sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
$ sudo ifconfig wlan0 up

```

By doing just 'that', (and nothing else), I can connect to the WISP antenna through my PC antenna and radio, and I'm on the net.

My IP address appears to change each time, but seems to always be on the 192.168.4.X portion (and I can 'see' my neighbors using sniffing tools on similar 192.168.4.X portions of the net). I 'think' that we're all on what they call the same 'subnet' (but I'm not sure of the terminology).

Now, the 'problem' is that I'm trying to replace the broken antenna and routerboard that the WISP provided with my own equipment. The WISP says I can do that but that they won't support me. 

I 'thought' it was as easy as replacing the old antenna and the old radio with a new antenna (19dBi planar) and new radio (Ubuquiti Bullet M2 HP); but I'm having trouble setting that up. So that's why I am trying to go to the basics and, as a first belated step, trying to UNDERSTAND what situation I'm in with respect to what my wireless ISP (WISP) is providing me.

I 'think' they have me behind a router because they told me a LOT of people share my external IP address and because I can see that they are giving me a class C (unroutable) IP address. 

Does this make any sense yet?

---

### Post by rocksockdoc on 2011-05-01
> **QLee said:**
> there is a NAT somewhere, generally we would expect to find it in the gateway/router

I'm sorry. I really don't understand a 'gateway'. I see the word used all the time, but, I really do not understand what it is (and what it means, to me, in my network). Even after googling it: 

Here's the [Wikipedia on "gateway]("http://en.wikipedia.org/wiki/Gateway_%28telecommunications%29")".
> Gateways, also called **protocol converters**, can operate at network layer and above. The job of a gateway is much more complex than that of a [router]("http://en.wikipedia.org/wiki/Router") or [switch]("http://en.wikipedia.org/wiki/Network_switch"). Typically, a gateway must convert one protocol stack into another.I'm trying to find the practical significance of this output as it relates to 'my' network.
```

$ route -n
...
Kernel IP routing table
Destination   Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.4.0   0.0.0.0         255.255.255.0   U     2      0      0 wlan0
169.254.0.0   0.0.0.0         255.255.0.0     U     1000   0      0 wlan0
0.0.0.0       192.168.4.1     0.0.0.0         UG    0      0      0 wlan0

```From that output, I'm confused what the significance (to me) of the 192.168.4.0 is and the (Gateway) 192.168.4.1? What is the significance (to me, trying to just understand my network) of those two IP addresses?

Is one of them the router that my WISP is using to assign my DHCP address of 192.168.4.whatever?
If so, what's the other address?

And, where did that 169.254.0.0 come from? It's not even close to the same domain.

Note: I understand the AND'ing of the masks but I don't understand what this command is fundamentally telling me about "my" network.

---

### Post by JKyleOKC on 2011-05-01
The 192.168.4.0 is your "network" address; what it means in this context is that any packet addressed to one of the 254 possible addresses on this subnet will be routed directly to that address rather than going through the "default gateway." Basically, the zero  bits of your netmask specify the size of your unique address, while the one bits of the mask identify the subnet address portion. Two of the unique address portions have special meanings and the others (254 in your case since the unique portion is 8 bits wide) are available to identify specific users. If all bits are zero, it's a "network" address and identifies the network rather than any specific user; if all are one, it's a "broadcast" address and all specific users will accept packets addressed to it.

Neither of the special addresses has much use to you as a user of the system but both are important in the internal handling of network packets.

The 169.254.0.0 address is another special meaning one that deals mostly with Windows clients; it's used when Windows' startup code cannot obtain an IP address for the system through more normal means. In other words, it's a default fallback. Apparently your WISP is using a Windows-based server.

Finally, the "default gateway" is, as the name applies, the real gateway from your subnet to the wider world of the Internet. It's the address of some device, probably at your WISP's site, that accepts data packets from you and passes them on to the next leg of their journey.

What the definitions you quote are leaving out is the fact that a network card on a subnet can communicate ONLY with other devices on that same subnet, unless the devices are listed by address in a routing table. The default gateway provides a device with much larger routing tables, that can pass packets from one subnet to another, thus moving them up the line and eventually to the "backbone" circuits.

To see this in action, use the "traceroute" command (which requires "sudo" to run) which will list all the hops the packets take in getting from your system to, say, [www.google.com](www.google.com). That may make much of what goes on more understandable...

---

### Post by bab1 on 2011-05-01
> **rocksockdoc said:**
> I understand. I really do. I think 'my' particular ISP has a weird setup. I knew nothing of all this until I had to replace the equipment. 

What I 'think' they have is they have all my neighbors and me on the same 'subnet' (I hope I used that word correctly). 

For example, I can eliminate all variables if I change the MAC address of my wireless card on my laptop to the MAC registered to my WISP. That way you can help explain to me what it is that I actually have (and which I'm trying to fix).

For example, let's assume DE:AD:BE:EF:CA:FE is the MAC address registered as mine for my WISP connection. If I place my laptop (with its puny 1dBi antenna and anemic 50mW wlan0 radio) in a window facing the WISP antenna 1,000 feet away, I can actually (sort of) connect. But I get their router (MicroTik brand) screen asking me to log into their router, which, of course, I can't. 

If I then simply change my Ubuntu PC's wlan0 MAC address to that which the WISP expects, I 'can' connect (and, in fact, I 'am' connected right now in this very manner).
```

$ sudo ifconfig wlan0 down hw ether DE:AD:BE:EF:CA:FE
$ sudo ifconfig wlan0 up

```

By doing just 'that', (and nothing else), I can connect to the WISP antenna through my PC antenna and radio, and I'm on the net.

My IP address appears to change each time, but seems to always be on the 192.168.4.X portion (and I can 'see' my neighbors using sniffing tools on similar 192.168.4.X portions of the net). I 'think' that we're all on what they call the same 'subnet' (but I'm not sure of the terminology).

Now, the 'problem' is that I'm trying to replace the broken antenna and routerboard that the WISP provided with my own equipment. The WISP says I can do that but that they won't support me. 

I 'thought' it was as easy as replacing the old antenna and the old radio with a new antenna (19dBi planar) and new radio (Ubuquiti Bullet M2 HP); but I'm having trouble setting that up. So that's why I am trying to go to the basics and, as a first belated step, trying to UNDERSTAND what situation I'm in with respect to what my wireless ISP (WISP) is providing me.

I 'think' they have me behind a router because they told me a LOT of people share my external IP address and because I can see that they are giving me a class C (unroutable) IP address. 

Does this make any sense yet?

I think you should look at this from a slightly different perspective.  It appears that what your WISP does is register you by MAC address.  

When you are only working with the LAN (subnet) you are on you communicate by IP to MAC address resolution.  This is ARP.  When you send a packet to an IP addreess that is not in your subnet there is no MAC address in the ARP cache.  The MAC address is the ultimate destination.  

If the MAC address is not located the data is sent to the subnet's router.  This is the gateway.  Many times this changes the Layer 2 (Ethernet) protocol to something else (ATM or Frame relay or SONNET).  In the old days this is what made it a gateway.  In todays world the term router and gateway are pretty much used for the same device.

```
$ route -n
...
Kernel IP routing table
Destination   Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.4.0   0.0.0.0         255.255.255.0   U     2      0      0 wlan0
169.254.0.0   0.0.0.0         255.255.0.0     U     1000   0      0 wlan0
0.0.0.0       192.168.4.1     0.0.0.0         UG    0      0      0 wlan0
```

Some explanation of the above:
[LIST]
[*]The term 0.0.0.0 means all interfaces
[*]The term gateway means the interface in the subnet that is connected to the router
[*]The term Genmask means the subnet mask of that interface (this defines the range of hosts in that subnet. Note that the 255.255.255.0 mask means 254 available hosts + the subnet ID and the b'cast address.  The 255.255.0.0 mask means 65534 available hosts + the subnet ID and the b'cast address. Try [**_[COLOR="DarkSlateGray"]this subnet calculator[/COLOR]_**]("http://www.mikero.com/misc/ipcalc/?start=") to see how IPv4 addressing works.
[*]The term Flags denotes what interface is up (U) or what is up and the gateway (UG)
[*] the others are either obvious or irrelevant here
[/LIST]

This will probably generate more questions, so ask away.

---

### Post by QLee on 2011-05-02
[QUOTE=rocksockdoc]I understand. I really do. I think 'my' particular ISP has a weird setup. I knew nothing of all this until I had to replace the equipment.[/QUOTE]

Doesn't seem that weird to me, seems like a good idea to reach remote or rural areas where there aren't other broadband options or to blanket an area. There is no reason for your ISP to make this easy to figure out.

[QUOTE=rocksockdoc]What I 'think' they have is they have all my neighbors and me on the same 'subnet' (I hope I used that word correctly).[/QUOTE]

That sounds correct, at first I wasn't understanding that the Senao is the "home router" you mentioned in your original post. My bad. 

[QUOTE=rocksockdoc]For example, I can eliminate all variables if I change the MAC address of my wireless card on my laptop to the MAC registered to my WISP. That way you can help explain to me what it is that I actually have (and which I'm trying to fix).[/QUOTE]

Then it looks like your ISP assigns your IP according to MAC. In the beginning, did you have to sign on in some way for the connection to be first established? ...Or, did they ask for your MAC and set it up manually themselves? It is probably good enough to think of the connection coming from what you term the "antenna" as a pipe to the Internet tied to a specific MAC.

[QUOTE=rocksockdoc]... But I get their router (MicroTik brand) screen asking me to log into their router, which, of course, I can't.[/QUOTE]

This is the sort of thing I was referring to above, was something similar to this necessary the first connection time but on a web interface page? Did you initally have to make a connection with a username and passphrase?
...

[QUOTE=rocksockdoc]My IP address appears to change each time, but seems to always be on the 192.168.4.X portion (and I can 'see' my neighbors using sniffing tools on similar 192.168.4.X portions of the net). I 'think' that we're all on what they call the same 'subnet' (but I'm not sure of the terminology).[/QUOTE]

Sounds to me like you've got it figured out. Be careful sniffing a network you don't own (depending on the laws in your area).

Basically I think for your present purpose you can just think of the connection from the ISP as "The Internet" accessable from a computer with a given MAC. 
...

[QUOTE=rocksockdoc]I 'think' they have me behind a router because they told me a LOT of people share my external IP address and because I can see that they are giving me a class C (unroutable) IP address.[/QUOTE]

Clearly they do, but what goes on at their end would be mostly transparent from your end and the radio setup in between is basically acting like an unreasonably long network cable (very much like plugging your computer into a network at a work site). 

I have no idea about how you would go about replacing their radio-to-network-node equipment with your own and lining things up so your end could communicate with their end. It is probably just some high gain antenna/amp to network card stuff. It seems to me what you need to do is have the correct MAC (or a clone of the correct MAC) in the device that makes the request for IP address from DHCP (the router at their end), and that would be sufficient for your stated purpose.

You might also try asking in the Networking & Wireless sub-forum, there might be someone who is using the same equipment, perhaps even the same ISP.

---

### Post by rocksockdoc on 2011-05-02
> **QLee said:**
> at first I wasn't understanding that the Senao is the "home router" you mentioned in your original post

To be clearer, the WISP provided the antenna & the Senao "radio" on the roof (where the Senao, I 'think', was configured as a bridge and not as a router but that's what I'm trying to determine).

That was wired through the attic to my "home router" which is your typical Linksys WRT54G set up with DHCP to supply the house. (So, to be clear, there are 'two' routers ... one inside the antenna enclosure and the other inside the house on a shelf.)

What I'm trying to do is UNDERSTAND the initial setup so that I can reproduce it with my own equipment (namely my own antenna and my own Ubuquiti "radio", either set up as a bridge or as a router depending on what the WISP originally set up for me). 

I went over, in detail, what you, bab1, and JKyleOKC kindly taught me, and, to give back to the forum, I'm creating a graphic which has all their explanations, with respect to my situation (to be posted when I finish it)

> **QLee said:**
> In the beginning, did you have to sign on in some way for the connection to be first established? ...Or, did they ask for your MAC and set it up manually themselves? 

They set up the equipment initially. I own the equipment but they set it up. The problem is they use crummy equipment and I want nicer stuff. When I asked them, they said all they need is the MAC address. Nothing else is needed (which I've proven because I can connect to them from my laptop without anything in between their transmitter and me).

> **QLee said:**
> Did you initally have to make a connection with a username and passphrase?

Nope. All they need is the MAC address of the receiving radio (which is attached to the receiving antenna on the rooftop). That's definitely all the WISP needs because I've proven that (and I'm familiar with the web-authentication setup you mention).

For example, at McDonalds or Starbucks, you can 'connect' to their network and their router will give you an IP address - but you're not 'authorized' yet so you have no access to anything more than their start page (which may or may not have a username/password field for you to fill in). 

This is like that - but - without the browser-authentication step.

For example, if I have the 'wrong' MAC in my radio (in this case, in the laptop when all my other equipment is powered down), I can "connect" to the WISP router (and I get a login/password page which is useless because that's their access to their router). If, on the otherhand, I change the MAC address of my radio (i.e., wlan0 inside my laptop) to the right MAC address, I no longer get their browser login screen - I'm directly on the Internet. No browser needed. No login needed. No password needed. Nothing but the MAC address has to be right. (Their rather abrupt support people told me this is how they work.)

> **QLee said:**
> Sounds to me like you've got it figured out

Not really. Even though their setup is diabolically simple, I 'still' haven't gotten my replacement antenna and radio to work yet. I'm still befuddled with trying to figure out if they had the Sendao radio set up as a bridge or as a router. It makes a huge difference because there are a million settings in the new Ubiquiti Bullet M2 HP radio attached to the new antenna.

> **QLee said:**
> Basically I think for your present purpose you can just think of the connection from the ISP as "The Internet" accessable from a computer with a given MAC

The only word I'd change is I'd change "computer" to "radio", as in:
> Basically I think for your present purpose you can just think of the  connection from the ISP as "The Internet" accessable from a 'radio'  with a given MAC

Right now, I'll concentrate on trying to understand if they had the Senao as a bridge or a router; and I'll post a picture of my results with the explanations given above.

Thanks for all your teaching!

---

### Post by QLee on 2011-05-02
[QUOTE=rocksockdoc]...
The only word I'd change is I'd change "computer" to "radio", as in:[/QUOTE]

When I wrote that, I meant at the end of the cable that you plug into your computer is like a long CAT-5 network cable in terms of operation (ie block diagram).


[QUOTE=rocksockdoc]Right now, I'll concentrate on trying to understand if they had the Senao as a bridge or a router; and I'll post a picture of my results with the explanations given above.[/QUOTE]

If I've understood everything correctly to this point, I would say they used it in bridge mode (without knowing what is in the antenna box equipment, it's just a guess) but it appears that your local IP (the x.x.4.x one) comes from the remote end not the Senao (the Senao only allows one connection at a time, is that correct).  If I guess correctly, you want your home router to distribute to more than one computer so it also sounds like what you need to do is clone the working MAC to the outfacing side of your home router (toward the bridge) so it identifies as the working MAC (this should be pretty much the same as connecting the computer with that MAC) and then you can setup your home router to DHCP for your LAN.

[Edit] They might be abrupt because they suspect you are trying to "pull" something. I would check the terms of service of your account they may not "allow" multi-seat distribution at your end, or might want to charge extra for it, or just want to discourage it  and it is likely first-tier support doesn't understand much anyway beyond what can be done from reading a script on their screen. And. sometimes people become abrupt and agressive because they don't have an answer and don't want to admit it for ego reasons, if you mentioned Ubuntu or Linux many tech support people aren't familiar with the OS and won't try to deal with such issues. I imagine they hate people trying to substitute their own equipment for "our" equipment, eh?

---

### Post by rocksockdoc on 2011-05-04
> **QLee said:**
>  I would say they used it in bridge mode (without knowing what is in the antenna box equipment, it's just a guess) 

I think you're right. There's nothing whatsoever in the antenna enclosure other than the antenna and the Senao unit. 

> **QLee said:**
> but it appears that your local IP (the x.x.4.x one) comes from the remote end not the Senao (the Senao only allows one connection at a time, is that correct).

I believe that to be correct. My WISP sends, through the air, 'only' 192.168.4.x to me when I'm authenticated by MAC address. The only thing that ever changes is the 'x' in the above number. It's always a 192.168.4.something each time I disconnect and reconnect.

> **QLee said:**
> If I guess correctly, you want your home router to distribute to more than one computer
Yes.

> **QLee said:**
> so it also sounds like what you need to do is clone the working MAC to the outfacing side of your home router (toward the bridge) so it identifies as the working MAC (this should be pretty much the same as connecting the computer with that MAC) 

Interesting. Are you intimating that, even though the "radio" in the antenna enclosure itself has two MAC addresses (one for the wireless side of the radio and the other for the LAN side of the radio), that, set up as a bridge, the settable MAC on the router will be 'seen' by the WISP (instead of the wireless side of the radio)?

The radio (whether set up as a bridge or router) on the roof has two MAC addresses:

[LIST]
[*]One MAC for the incoming WLAN wireless signal coming from the antenna
[*]One MAC for the single outgoing LAN data + power wire that tunnels through the attic to my home router
[/LIST]
 The home router (Linksys WRT54G) has three MAC addresses:

[LIST]
[*]One MAC for the incoming wired "Internet" port (which is the 'data' wire from the POE box)
[*]One MAC for the four outgoing LAN Data" ports (which go to equipment in the house)
[*]One MAC for the outgoing WLAN coming out of the home router (and serving the home computers wirelessly)
[/LIST]
Of those three home router MAC addresses, only the first one is user settable. 
Of the two radio MAC addresses, only the WLAN one connected to the antenna is settable - but - here's the clincher - but only when in Router mode (that is, in Bridge mode, the MAC of the WLAN on the radio is not settable).

So, are you saying there is a way for the WISP to 'see' the MAC set in the home router 'through' the two MACs on the radio on the roof connected to the antenna?

Because that is what I wanted to set up (but failed):

[LIST]
[*]Signal comes from WISP (e.g., 192.168.4.50)
[*]WISP sees the registered MAC address & authenticates
[*]Radio passes signal from it's WLAN to it's LAN in Bridge mode & feeds that to the home router Internet port
[/LIST]
The problem is that I can only get the WISP to authenticate with the radio in router mode because that's the only mode that supports changing the MAC address that the WISP sees.

If I could understand how to get the home router's MAC to be seen by the WISP with the radio in bridge mode, that would be an achievement!

---

### Post by rocksockdoc on 2011-05-04
> **QLee said:**
> [Edit] They might be abrupt because they suspect you are trying to "pull" something. 

Nah. I've been totally up front with them. And, they were rude when I started with them long ago. Two of my neighbors told me they were obnoxious so they switched to a different provider. So, it's a well-known 'attitude' of this particular company. So far, I just avoid them. Luckily, it's rare that I ever need to talk to them. But, when I do, it always leaves a bad taste in my mouth.

Another reason might be that the WISP technical support personnel, while I only know them by telephone, have been suggesting I buy 'their' equipment and use their supplier. They didn't like it at all when I said I was using wlanparts.com. They had a local supplier they wanted me to use. I think they're just not getitng their 'cut' of the results. They say I can put my own equipment in, but they don't want to support it. They have this feeling that only they can do this (and maybe they're right - but I want to at least try on my own).

I'm not sure what 'multi-seat distribution' is, but my speeds are so low that I would not wish my Internet on anyone else! :)

> **QLee said:**
> [ I imagine they hate people trying to substitute their own equipment for "our" equipment, eh?

I think that's a good part of it. 

The good news is that I have it working now - with the radio set up in router mode because that allowed MAC cloning.  I really wanted to put the radio in Bridge mode ... but the radio just won't allow the WLAN MAC to be set while it's in bridge mode. Sigh.

The steps I performed to set this up were the following from the radio manufacturer's support team:
> 
[LIST=1]
[*]Plug a 15vdc or 24vdc POE power + data cat5 cable into the Bullet M2 HP
[*]Hold the Bullet M2 HP "reset" button for about 15 seconds (until lights flash)
[*]Connect the data cable of the POE to the RJ45 port of the laptop computer
[LIST]
[*]Note: Tested on *Firmware Version: XM.v5.3 Build Number: 7782*
[/LIST]
[*]Set the IP address of the laptop computer's NIC to 192.168.1.10
[LIST]
[*]*Note, on Linux, as root, use: $ ifconfig eth0 192.168.1.10*
[/LIST]
[*]Open a web browser to [http://192.168.1.20]("http://192.168.1.20/") (username=ubnt, password=ubnt)
[*]Navigate to the Bullet M2 HP "Wireless" tab
[LIST]
[*]Note: The link is titled the "*rb411routerboard: [Bullet M2] - Setup Link*"
[/LIST]
[*]On that tab, set the Bullet M2 HP "Wireless Mode" to "Station".
[*]For "SSID", click "Select" & choose a WISP AP of at least -55dBm to -75dBm
[LIST]
[*]*Note: My WISP was -30dBm which was a great signal (100% CCQ)!*
[*]*Note: I had to hit "Select", "Change", & "Apply", in sequence, to effect the change.*
[/LIST]
[*]Navigate to the Bullet M2 HP "Network" tab
[LIST]
[*]Note: The link is titled the "*rb411routerboard: [Bullet M2] - Network Setup*"
[/LIST]
[*]Set the Bullet M2 HP "Network Mode" to "Router"
[*]Set the incoming "WLAN Network Settings" "WLAN IP Address" to "DHCP"
[*]Click the "Change MAC Address" checkbox & set the MAC address to that which your WISP authenticates upon
[*]In the outgoing "LAN Network Settings" section, set the "IP address"  & "Netmask" to something like "192.168.10.20" & "255.255.255.0"  respectively
[*]Check the outgoing LAN "Enable NAT" checkbox
[*]Check the outgoing LAN "Enable DHCP Server" checkbox
[*]Set the outgoing LAN "Range Start" and "Range End" to something like "192.168.10.100" & "192.168.10.200" respectively
[*]Hit "Change" and "Apply" in sequence to effect changes
[/LIST]
That sequence should get your single laptop PC on the Internet,  with the radio MAC authenticated by your WISP. To complete your network,  disconnect the cat5 cable from the RJ45 port of your laptop and connect  it to the incoming "Internet" port of the home Linksys WRT54G router  and configure that router as desired.

Note the new address of your Bullet M2 HP will be, in this example, [http://192.168.10.20]("http://192.168.10.20/") (and not [http://192.168.1.20]("http://192.168.1.20/") as it was originally configured).

Good luck! 			 		

---

### Post by rjdaggett on 2011-08-16
That 2nd DNS server is one of google's free DNS servers. FYI

---

