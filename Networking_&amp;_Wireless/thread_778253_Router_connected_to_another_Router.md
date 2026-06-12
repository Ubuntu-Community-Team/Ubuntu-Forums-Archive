---
title: "Router connected to another Router"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Sugi on 2008-05-01
I am trying to run internet through a second rounter.  Now, you may ask why?  I have a reason to my madness, let me explain. :)

The whole house gets internet from Router A and that one ethernet that comes from Router A is linked to my office.  I need that ethernet cord to be plugged into Router B and provide internet for my whole office.  Router A provides IPs to all of the house's computers and while Router B acts more like a hub to split up the internet to my computers within my office.  I have heard this is possible through having the router be either DHCP or not, but how do I do that?

This may make it even more confusing, but if I have to, I could make Router B more like a router and have it assign IPs to my office only.  Is that possible?  Or is it better?

P.S. if it matters, I have both Windows and Linux in my office.  All of them needs the internet from Router B.

Thank you so much for your time,
Sugi

---

### Post by rogblake on 2008-05-01
> **Sugi said:**
> I am trying to run internet through a second rounter.  Sugi

As long as the 2 LANs are set up on different subnets it should work OK. (You need different subnets for routing to work, for example set the LAN for router "A" to be 192.168.10.*, set router "B" to be 192.168.11.*.)

---

### Post by MaindotC on 2008-05-02
Dude - he actually thinks they are routers, he refers to the cat v cable as "ethernet", and says a hub "split up the internet".  I don't think he'll know what subnets are.

Sugi - I apologize that I do not speak your language but I will try to explain.  First try logging into router A by connecting the ethernet then type in a browser [http://192.168.1.1](http://192.168.1.1)  Do this when the other computers do not need to use the internet.  It should ask you for a username and password.  If you don't know the username and password, you can probably find it from the default password list [http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html).

There should be an option somewhere that says "Use DHCP" or "Enable DHCP".  Disable DHCP.  Restart router.

You know what this is going to take way more time to explain than I have time.  Forget it.

---

### Post by helgman on 2008-05-02
> **Sugi said:**
> The whole house gets internet from Router A and that one ethernet that comes from Router A is linked to my office.  I need that ethernet cord to be plugged into Router B and provide internet for my whole office.

Question 1: What is "the whole house"? Is it an office building or your house or something else? That is, what else is connected to Router A?

> Router A provides IPs to all of the house's computers and while Router B acts more like a hub to split up the internet to my computers within my office.  I have heard this is possible through having the router be either DHCP or not, but how do I do that?

Question 2: Might not be just that simple ... what kind of "routers" are we talking about here? Simple home gateways with one WAN-interface and four LAN-interfaces or are we talking a bit more competent pieces of networking equipment?

> This may make it even more confusing, but if I have to, I could make Router B more like a router and have it assign IPs to my office only.  Is that possible?  Or is it better?

This all depends on the answer to the above questions and your goals. If you are using a home gateway and you don't want computers connected to Router A initiating connections to your computers attached to Router B then yes, this might be better. Just make sure to configure Router B to use another subnet ([Wikipedia](http://en.wikipedia.org/wiki/Subnetwork)) than Router A.

Think about what you want, answer the questions and then we'll see if anyone can help you. It might also help with a little more information about Router A and Router B.

Regards,
Helgman

---

### Post by Sugi on 2008-05-02
helgman, I am sorry for leaving out so much details.  I only omitted what **I** thought wasn't needed, but I am wrong.

Question One:  This is my only house with three computers connected to Router A and within the office (aka computer room in the house) has three more computers connected to only Router B.

Question Two:  Router A is a Netgear WNR834B.  Router B is a Linksys BEFSR41.  Of Course, the Netgear has only one WAN, four LANs, and Wireless.  Router B has only one WAN and four LANs.

I would like my three computers to have their own network on Router B and this would be a complete different network from Router A.  I need to have all three computers on Router A and all three computers on Router B to have internet and a network.  To make this a bit more advance, I can not get wireless internet working on Linux from WNR834B (but I can get wireless internet working on Windows from WNR834B), but I do have an extra WRT54GS Linksys lying around.  If I could get wireless internet working on Linux from the WRT54GS that would be amazing.  But that is only extra, and I need internet working first for my office, because I can't get anything from Router B.

strAlan, are you extremely rude.

Thank you,
Sugi

---

### Post by Sugi on 2008-05-02
Actually, I am.  I am setting up two routers and I have never done this before.  :)

Sugi

---

### Post by Sugi on 2008-05-02
Bump

---

### Post by helgman on 2008-05-03
> **Sugi said:**
> I would like my three computers to have their own network on Router B and this would be a complete different network from Router A.  I need to have all three computers on Router A and all three computers on Router B to have internet and a network.

That should not be a problem. The Netgear (Router A) should default to subnet 192.168.1.0/24 (I think I linked to the Wikipedia article about subnets in my previous post) so you can leave it as is. It should also default to IP address 192.168.1.1 (good to know).

*Before you start remember that whenever you are trying to log in to a device, your computer needs to be on the same subnet as the device (if you are directly connected to it). So, if you at any time find yourself unable to connect, first investigate your computers IP address.*

*Problem A*: Router A hands out all addresses in subnet 192.168.1.0 except it's own (at leased that's how I remember Netgear and what the manual says).

*Solution A*: You have to log in to Router A (Defualt [http://192.168.1.1](http://192.168.1.1)) and navigate to "LAN IP Setup" or something like that. Change the settings under "Use Router as DHCP Server" so that the range don't include all addresses from 192.168.1.2 to 192.168.1.254. Leave out at least one address and save it for Router B (that is, change the range so that it starts with 192.168.1.3 or ends with 192.168.1.254 or change it some other way as long as you keep a range that holds enough addresses to serve the number of computers connected to Router A).

*Problem B*: The Linksys (Router B) defaults to the same settings.

*Solution B*: Connect a computer directly to one of the LAN-ports on Router B. Open the setup page ([http://192.168.1.1](http://192.168.1.1) by default). Now, for Internet Connection Type (or whatever it's named) chose "Static IP" and then fill in the wanted information. First of, you need an IP address that don't conflict with the once handed out by Router A (or the one held by Router A). Pick one that is not 192.168.1.1 or within the range handed out by the DHCP Server on Router A. I'll take 192.168.1.2 as my example.

Set the Subnet mask to 255.255.255.0 and the default GW to 192.168.1.1. As for DNS Server you can either look at what Router A or computers connected to Router A uses or you can search for addresses to OpenDNS servers. I'm fairly sure that Router A can work as a relay ... but do some investigation if you want to be 100% sure.

Now, change the LAN settings. WARNING! When you change the LAN setup and hit what ever the name of the button that saves and changes the settings, you'll (most likely) loose your connection.

Pick a subnet for the LAN connected to Router B (I'll go with 192.168.2.0/24). Then, configure the router. Example configuration could be:

IP address: 192.168.2.1
Subnet mask: 255.255.255.0
Local DHCP Server: Yes
Start IP Address: 192.168.2.100
Number of Addresses: 100
Client Lease Time: 0

Save the settings, the connect Router B to Router A via the WAN connection on Router B and a LAN connection on Router A. Attach a client to Router B and a) make sure that it hands out addresses with correct settings and b) make sure that the settings works as intended.

> To make this a bit more advance, I can not get wireless internet working on Linux from WNR834B (but I can get wireless internet working on Windows from WNR834B), but I do have an extra WRT54GS Linksys lying around.  If I could get wireless internet working on Linux from the WRT54GS that would be amazing.  But that is only extra, and I need internet working first for my office, because I can't get anything from Router B.

OK ... I can help you with the infrastructure and then maybe you should try a new post for help with the connection (there are a lot of people around that are way better with wireless).

*Question A*: Why don't you use the WRT54GS instead of the other Linksys as Router B?

If you are going to build on the previous setup, just logging in to your WRT54GS (let's call it AP) and change the settings (default is [http://192.168.1.1](http://192.168.1.1) so make sure your computer has an IP address in that range when you try). You don't need a WAN address since you won't be using that interface. For LAN you can try something like:

IP address: 192.168.2.2 (outside the DHCP range of Router B)
Subnet mask: 255.255.255.0
Local DHCP Server: No

Connect it to Router B via LAN interfaces on both devices.

For the wireless, start with setting up the basics (ESSID etc), but set it up with no encryption. Verify that you can connect with a client. Next, make sure to use the best encryption technique available to you, that's my advice. Then verify that you can connect again.

And you are done ... I think.

Does this solve your problem?

Regards,
Helgman

---

