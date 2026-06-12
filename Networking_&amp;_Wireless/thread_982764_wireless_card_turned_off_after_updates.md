---
title: "wireless card turned off? after updates"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by greymoose58 on 2008-11-15
I've got a Compaq Presario C793VU Laptop. When I purchased it the OS was Vista. Obviously I HAD to get rid of that. It was replaced with Hardy.

I knew that some people had to do a bit of hacking to get the wireless card (Atheros AR242x) working in the past so I was prepared to do that and I got it all up and running using madwifi.
Then I ran the necessary updates and lost the wifi connection. Madwifi didn't work so I resorted to ndiswrapper. I now have the network icon showing a network available but I can't access it. (Cable network is working fine.)
The wireless light is orange which apparently means that the card is turned off but I honestly think it has been orange all along.
[LIST]
[*]The card shows up with both lshw and iwconfig. 
[*]Pinging the router comes back with NETWORK UNREACHABLE.
[*]ARP shows the router's IP address but has 'Incomplete' in the name section
[*]Scan shows nothing even though the router is broadcasting about a metre and a half away.
[*]Security on the router is down to MAC filtering at the moment.
[/LIST]
There is a PC using a more sensible Linksys Wireless Card that isn't having any trouble so I relly think the problem is with the laptop.
I gather that this card may work better in 8.10 but I would like to stick with Hardy if I can as the machine is used for our business and I like the LTS option. If I can't, oh well.

If anyone has any ideas of how I might work around this I'd appreciate some guidance.

Ok, it is the next morning and wireless is working. I guess it needed one _more_ reboot. (By the way, the wireless light is still orange.)

---

