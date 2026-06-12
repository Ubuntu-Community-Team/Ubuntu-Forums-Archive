---
title: "DHCP server question"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by harisund on 2008-08-13
So I have my Ubuntu box wired as a internet-sharing router with a DHCP server installed. 

On the private LAN side, I have connected a switch, and to that switch are connected 2 wireless access points, and 2 desktops. Both the desktops get their DHCP from the Ubuntu's LAN subnet, and any machine connecting through the access points get their DHCP from Ubuntu itself. 

Now here's the question. Is there anyway I can detect through which wireless AP a DHCP request was made? Typically what I have done is protected one AP through a WEP key and left the other one unsecure. I want to know who connects through either. 

I basically want to do something like this. If somebody connects through my secure AP, give them a DHCP address in the 192.168.5.100-200 range. If someone connects through my unsecure AP, give them a DHCP address in the range of 192.168.5.50-192.168.5.90 . Then use iptables to mess around with the people connecting to my 50-90 network. Possible? 

(And for the record, I am using dnsmasq as my DHCP server, sharing the internet using iptables)


(EDIT: I guess one way of doing this would be to add another ethernet NIC to my Ubuntu box, connect one access point on each NIC and hand out different IPs based on which NIC the DHCP request is coming from .. but what otherwise?)

---

### Post by jimv on 2008-08-13
I'm not a networking guru, I've never done anything like that, and in fact this could be completely wrong, but here's my idea.  I think that you could look at the packets coming in and see which ones are coming through from each router's mac address.  Try running Wireshark with just the two routers connected to the server, and then connect a client to one of the routers.  See if there's anything in the ensuing network traffic that would tell you which router the machine connected to.

---

### Post by harisund on 2008-08-13
Hey that's actually a pretty neat idea. The concept of checking for the MAC address of the source from where the packet originated from was something that never struck me. 

Thanks a bunch! I will test it out later when I get back home and reply back.  This could probably keep me busy all weekend :)

---

### Post by harisund on 2008-08-13
I haven't yet tested it, but a quick thought struck me. Won't the MAC ID I will be seeing that of the switch, and not of the access points?

If I understand correctly, MAC addresses are passed down device to device right? The packets coming to the private NIC are essentially from the switch (to which the 2 Access Points are connected), right?

---

### Post by bab1 on 2008-08-13
The switch does not have a MAC.  It has no IP addr either.  :-)

A quick way is to run 2 nets on the same wire.  How 'bout 192.168.5.* AND 192.168.10.* ?  Then it would be obvious.  They also need to be bridged to be able to see each other.

Why this way?  Check out how the request for a DHCP IP address is handled

---

### Post by harisund on 2008-08-13
> **bab1 said:**
> The switch does not have a MAC.  It has no IP addr either.  :-)
oh ok! Thanks! Shows my ignorance :)

> A quick way is to run 2 nets on the same wire.  How 'bout 192.168.5.* AND 192.168.10.* ?  Then it would be obvious.  They also need to be bridged to be able to see each other.
I have a question. My LAN IP address on my Ubuntu box is 192.168.6.1. Therefore, when the machines request an IP, they are at the moment given something in the range of 192.168.6.100 to 192.168.6.200. Their gateway and DNS are both set to 192.168.6.1 itself. 

Now 2 questions- 
a) If I were to assign 192.168.5.* and 192.168.10.* do I have to make any client side changes to route to 192.168.6.1 as their default gateway? I don't want my room mates to do anything, basically they just plug in the LAN cable and start surfing (fun being the only geek in a house), or just connect to a network from a list and get connected. I assumed all the devices have to be in the same subnet as the router. I guess the network mask changes from 255.255.255.0 to something else then? 
b) Even if I were to somehow make the above work, how do I say "all clients requesting DHCP through ACCESS_POINT_1 should receive 192.168.5.*" and "all clients requesting DHCP through ACCESS_POINT_2 should receive 192.168.10.*" ? 

(And just for information, my wireless access points are essentially wireless routers with their DHCP server option turned off, and using a cross over cable :P)

---

### Post by bab1 on 2008-08-13
Lot's of questions here.  I will edit this post in a little bit.  Give me about 1/2 hour.  :-)

Edit1:
> do I have to make any client side changes to route to 192.168.6.1 as their default gateway?
It can all be handled at the Ubuntu DHCP server.  You will have to bridge the networks if you want to see each other.  Do you want that functionality?

> I guess the network mask changes from 255.255.255.0 to something else then? 

The net mask stays the same.  It basically describes  which part of the IP address is network (192.168.5.*) and what is the actual address in the network (192.168.5.[COLOR="Red"]1 - 254[/COLOR]).

> Even if I were to somehow make the above work, how do I say "all clients requesting DHCP through ACCESS_POINT_1 should receive 192.168.5.*" and "all clients requesting DHCP through ACCESS_POINT_2 should receive 192.168.10.*" ?

Ahhhh, here's the rub.  All of your roommates  can request an IP address through BOTH AP's  So let's not bridge.  We will keep the groups separated (guests and roommies)  Give each on their own net and allow the dhcp services be network specific.

> And just for information, my wireless access points are essentially wireless routers with their DHCP server option turned off, and using a cross over cable :P)

Save the last for the best.  You can use the wireless routers as routers or run multiple DHCP servers on your gateway.  The DHCP server will hand out the DNS and Gateway info.

I would use the wireless as routers and then you can point them towards your 6.1 gateway.  Using the Ubuntu host as the DHCP server and GW you will have to bridge that specific host to all the nets.

---

### Post by harisund on 2008-08-13
Awesome, take all the time you want. I am really grateful for you having taken the time and patience to do it.

---

### Post by bab1 on 2008-08-13
See if the edits in post #7 answers your questions.  Be sure you have a clear idea of what to do before you start.  Ask more if needed.

Edit1:  I just had a thought.  Leave the encrypted router(AP) as it is.  We know it works.  You can config the other for guests as needed using the examples in post #7.  This way we preserve the 192.168.6.* network (actually SB written as 192.168.6.0/24)

---

### Post by harisund on 2008-08-13
I am going to study a little bit in detail regarding bridging before I get back to you. 
Meanwhile, here's my network topology at home 

[http://img187.imageshack.us/my.php?image=topologyro5.jpg](http://img187.imageshack.us/my.php?image=topologyro5.jpg)

My original wish is to separate the guys on the "unsecured" network from the guys on the secured network. For example, the guys on the secured network (and the 2 desktops in the picture) go through a transparent squid proxy and are allowed bit torrent capabilities, while guys on the unsecured network are prevented from stuff like that.. What do you recommend is the best way to do that? Use the access point as a router directly? 

In any case give me more time to go over your post in depth :)

---

### Post by bab1 on 2008-08-13
i could allready see your setup in my mind.  I'm looking at it from a virtual point of view.  Your drawing is its physical layout.  Are you a CS major?  I can discuss the points via IM later in the day if you wish.

---

### Post by harisund on 2008-08-14
I am a masters student in electrical engineering actually, just interested in Linux, that's about it.

My IM ID is harisund on any messenger service, though today I am probably going to be busy because its orientation day for new kids in my university and I am going to be volunteering to help them. 

That said, I really appreciate your help and any suggestions you have.

---

### Post by bab1 on 2008-08-14
I have added you to my buddy list for AIM.  Let me know when you are available.  I have attached a modified version of your "napkin net" to this posting.  :-)

---

