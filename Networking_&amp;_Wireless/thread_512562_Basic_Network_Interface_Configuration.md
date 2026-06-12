---
title: "Basic Network Interface Configuration"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by regnumimbrium on 2007-07-29
Hey All,

I'm taking a shot in the dark at installing and configuring a home server to host a personal website (and maybe later host files/printers for my household). So far I've got Ubuntu Server Edition 7.04 installed successfully and right now am working on configuration of my primary network interface. Unfortunately, the most basic understanding of how this all works escapes me and - after an hour of searching - apparently much of the internet. Here's what I'm looking at (in vi editor):

# The primary network interface
auto eth0
iface eth0 inet static
        address xxx.xxx.xxx.xxx
        netmask 255.255.255.0
        network xxx.xxx.xxx.xxx
        broadcast xxx.xxx.xxx.xxx
        gateway xxx.xxx.xxx.xxx

My problem is that I don't know what goes where. I have a couple other computers behind a Linksys router which is connected to my modem/cable line. Again, I primarily want to host a personal website and only in the distant future would consider file/printer hosting on my home network. Using "www.whatismyipaddress.com" I've got my current ip address and, after I check my router's settings, I'll figure out which "router address" my server has (i.e. 192.168.1.10x or whatever). Can someone tell me how this all fits in up there (and *why*, if so inclined)?

Thanks very much!
-ri

---

### Post by mips on 2007-07-29
Why are you using xxx for private ip addresses as there is no risk to you ? This way we have no idea what you configured either.

You might have to do port forwarding for a web server but I'm not sure to be honest.

---

### Post by regnumimbrium on 2007-07-29
Oh, sorry, I was just being generic and didn't really know or not if there would be any risk to me. But the point is that I didn't configure anything there, yet; I don't really know what should be going in there. I'm using the "Perfect Setup" tutorial which can be found here (the page that I'm on):

[http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3)

Anyway, the author's configuration is this:

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

But it doesn't specify whether I should use the ip address assigned to the computer by the router or the ip address assigned to my household in the "address" row. Also, except for netmask, I don't understand why network, broadcast, and gateway look the way they do and what they'd look like if the author had used a non-router-assigned ip address (sorry if that's incorrect lingo). Any other suggestions?

Thanks Again,
-ri

---

### Post by Synflux on 2007-07-29
Hi,

I'm taking some guesses here as to your setup but hopefully this will point you in the right direction.

1. Address:
What address is assigned to you by the router? Something in the range 192.168.0.x at a guess? You could use that address but the danger is that the router then hands the same one out to another computer (not knowing you are using it) and that would result in an ip conflict.  Normally I'd choose something well out the way (say 192.168.0.254) that should never be used by the router.

Do not use the address given to you by whatismyip, this is called your WAN or Public address and is not what you should be using here.

2. Netmask: Leave this as it is. This is a standard class C address which basically means you can have up to 254 hosts on your subnet/segment.

3. Network: This is the network ID, in your case of a standard class C it will be 192.168.0.0 if your router hands out addresses in the 192.168.0.x range.

4. Broadcast: This is used to address all hosts (computers) within a subnet, in your case this will be 192.168.0.255 as it is always the last possible address in the subnet.

5. Gateway: This is used when your computer needs to access computers outside it's own subnet. For your purposes it is the private/LAN ip address of your linksys router. Most likely this is 192.168.0.1

I hope that helps you, if you have any further questions please ask. :)

---

### Post by regnumimbrium on 2007-07-29
Great info Synflux, thanks a lot.

Based on what you've said and that my router seems assign ip addresses in the 192.168.1.x range, I'm guessing my configuration should like something like this:

address 192.168.1.254   [or 192.168.1.104]
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

How does that look? 

Also, I understand the risk of an ip conflict I choose 192.168.1.104 to be my address but I don't understand in what instance that would happen. If my server is always on and connected to the router wouldn't it always assigned a number around that one? I'd be happy to just choose 192.168.1.254 but I don't quite understand how it is that I'm allowed to "pick" my own ip address (and that's probably an advanced topic which you don't have to spell out for me here [but, again, you're more than welcome to!]); I also don't know if choosing 192.168.1.254 would mean I'd have to make additional changes in my router settings. Is there an easy explanation to all that?

Thanks Again!
-ri

---

### Post by Synflux on 2007-07-29
Hello,

Yes, the example config in your last post looks fine.

The reason for the possible conflict is that the Linksys router is handing out addresses to computers that ask for them using a protocol called DHCP. However, in your first post you put: 

iface eth0 inet static

Which means that your server won't use DHCP to ask for an address, it will just use the one that you've specified. I think the linksys' hand out addresses from 100 upwards so therefore if you plugged 5 computers in then it would hand out 104 to the fifth one, not knowing that you are using it.

If you choose a number between 2 and 99 then you should be safe as the Linksys will never hand these out (by the sounds of it).  You won't have to change any settings. If you need to forward any ports then you just forward them to the address you've chosen.

Hope that helps you, again please ask if any further questions. :)

---

### Post by regnumimbrium on 2007-07-29
Thanks again! It seems to have worked fine. I'll probably repost in a day or so if I run into more network problems. :)

-ri

---

