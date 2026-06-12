---
title: "Help setting up connection manually, dsl router + wireless"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by spock84 on 2006-11-24
I get my internet connection from the people I rent my room from, who live upstairs, so I have no physical access to either router, but I've got user/pass for the dsl router (SpeedTouch). Now when I use DHCP I can't get into active mode in any apps, which is a bit of a drag, but right now it seems it's my only option. My computer then gets an 192.168.1.* ip, which I guess means it's straight from the wireless router/AP (Topcom). Before I could set my ip to whatever 10.0.0.* adress I wanted, netmask 255.255.255.0 and DNS 10.0.0.1, but they recently replaced the DSL router (albeit the same make and model, so it shouldn't make much difference) and everything seems to be connected the exact same way (though the AP now is 10.0.0.3, not 10.0.0.4 on the DSL router), but for some reason those manual settings won't work now.

So most importantly 1) How can I fix this? and 2) Is there a default password for Topcom AP's? I remember trying some that I found on the net, but they didn't work.

---

### Post by FrodoB on 2006-11-24
Have they locked your MAC identifier out?

---

### Post by spock84 on 2006-11-24
I don't know much about this stuff really..

But no, I don't think they have. They're 100% incompetent. They've just plugged it in, hoping it would work.

---

### Post by spock84 on 2006-11-25
Bump :)

---

### Post by FrodoB on 2006-11-25
Maybe someone with some thoughts on this can jump in.

---

### Post by spock84 on 2006-11-27
Okay, I've now got access to both routers. I got to reset the wireless one and found the standard user/pass. What should I look for?

What I noticed though was that in the network settings, there used to be lots of stuff in the "hosts" tab, back when I ran Dapper. After I switched to Egdy it has been empty. Could it be that this is the problem and not with the routers?

---

### Post by FrodoB on 2006-11-27
You do have the Ubuntu side configure to use DHCP and the router does have the DHCP server activated correct?

---

### Post by spock84 on 2006-11-27
As I said, I don't really know anything about routing, but when ubuntu is configured to use DHCP it works, but I can't get an active connection with it.

On the Topcom (the AP) LAN settings are as follows:
IP: 192.168.1.1
Subnet mask: 255.255.255.0
DHCP Server: Enabled
Start IP: 192.168.1.100
End IP: 192.168.1.199

In the "WAN" tab it says:
Connection type: DHCP Client or fixed IP
WAN IP: Obtain IP Automatically


Then there's a section called "Routing". In "Static" and "Routing table" there are no entries, and in "Dynamic" it says:
NAT: Enabled
Transmit: Disabled
Receive: Disabled

After that there's a section called "Access" which has all sorts of filters and firewall rules, which I guess is the problem with respect to the 192.168.1.* ip's me and the other get. I'll try opening some ports there, and check back here eventually.

Any idea what "Special AP" is? Looks like there are some entries for certain applications there too, just like in the firewall rules tab.

---

### Post by FrodoB on 2006-11-27
I suggest that you report the exact make, model, and version of router access point back to this list and perhaps someone can offer advice.

---

### Post by spock84 on 2006-11-27
All I remember is that it's a Topcom Skyr@cer, not the exact model, but I'm guessing the interface is pretty similar on all of them?

---

### Post by FrodoB on 2006-11-28
I don't know anything about that one.  Maybe you can get the manual in PDF format from the manufacturer's web site and that will tell you what you need to know?

---

### Post by spock84 on 2006-11-30
Still having problems figuring this out. ](*,)

---

### Post by FrodoB on 2006-12-01
You cannot set your address to whatever you want to.  Let the router assign it throught DHCP, that is what it is for.  The address that is gives you should be sort of semi-permanent as it likely hands them out by MAC address. You can probably lock that down in the DHCP section of the router's setup pages.



> **spock84 said:**
> I get my internet connection from the people I rent my room from, who live upstairs, so I have no physical access to either router, but I've got user/pass for the dsl router (SpeedTouch). Now when I use DHCP I can't get into active mode in any apps, which is a bit of a drag, but right now it seems it's my only option. My computer then gets an 192.168.1.* ip, which I guess means it's straight from the wireless router/AP (Topcom). Before I could set my ip to whatever 10.0.0.* adress I wanted, netmask 255.255.255.0 and DNS 10.0.0.1, but they recently replaced the DSL router (albeit the same make and model, so it shouldn't make much difference) and everything seems to be connected the exact same way (though the AP now is 10.0.0.3, not 10.0.0.4 on the DSL router), but for some reason those manual settings won't work now.

So most importantly 1) How can I fix this? and 2) Is there a default password for Topcom AP's? I remember trying some that I found on the net, but they didn't work.

---

### Post by spock84 on 2006-12-01
Okay. That's pretty much what I've figured out.

But what remains then is to get an active connection. I've tried opening all ports for the AP in the DSL router and all ports ingoing and outgoing seem to be open on the AP, but doesn't seem to help much. When I was assigned an IP from the DSL router (10.0.0.*) everything was automatically forwarded straight to my computer, but now there's like a second NAT thing to set up, and I just can't figure out how to do that. I tried looking in the manual, but it doesn't make much sense to me. You see what I mean? Now traffic has to go through two routers before reaching me.

---

### Post by FrodoB on 2006-12-01
It is working for the owner's purposes, correct? Maybe you could take a look at the network settings on one of their machines that works to see if you are setup correctly?

---

### Post by spock84 on 2006-12-02
I solved the problem. It was in the "Special AP" section on the wireless router. "This screen enables you to specify special applications, such as games, that require multiple connections that are inhibited by NAT." I can't believe I overlooked that.. ](*,) Everything's working smoothly now.

---

