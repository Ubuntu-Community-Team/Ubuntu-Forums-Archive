---
title: "Internet problem over WLAN"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by iago1983 on 2008-08-03
Hi there,

I am running Ubuntu 8.04 on a HP Compaq 8510p laptop, with an on-board Intel wireless LAN adapter. 

I am able to browse the net fine through a wired connection and using my 3G USB Huawei modem connection. When I do try doing this over WLAN though, it appears to connect to the webpage and begin the GET, before dropping out after about 5-10 seconds. 

I'm a Microsoft consultant coming over to the dark side :) so have checked all the standard network bits and pieces - DNS is functioning, connections can be made to the site and to the local WLAN without issue. I tried adding a static ARP mapping for my WLAN router (a modified Option box, being used in Australia on Virgin Broadband@home) as per a couple of other posts I have found but with no luck.

I have done a wireshark capture (attached) which seems to indicate that all is well initially, but then for some reason my router reprompts for the MAC address of my laptop WLAN adapter (IP is 192.168.1.44; router IP is 192.168.1.1) which is typically when it fails.

Can anyone shed some light on this by any chance? Any advice much appreciated :)

Cheers,

David

---

### Post by caljohnsmith on 2008-08-04
> **iago1983 said:**
> I tried adding a static ARP mapping for my WLAN router (a modified Option box, being used in Australia on Virgin Broadband@home) as per a couple of other posts I have found but with no luck.
David, would you please clarifying for me what you mean by "a static ARP mapping for my WLAN router"? Are you saying that computers on your WLAN are mapped to a set IP address based on a MAC address table you have set up or something? I'm thinking this has something to do with your problem because you say:
> ...but then for some reason my router reprompts for the MAC address of my laptop WLAN adapter (IP is 192.168.1.44; router IP is 192.168.1.1) which is typically when it fails.
So your router sends an extra ARP request to your computer, and then things fail?

---

### Post by iago1983 on 2008-08-05
Hey, thanks for replying :)

By static ARP mapping I mean I used arp -s to try and add an ARP mapping for my router's IP on the laptop; so I entered in a terminal on the laptop:

arp -s 192.168.1.1 00:11:22:33:44:55 

where the MAC address was that of the router.

I also tried lowering the MTU (down to 1400) on the laptop wireless, router wireless and router WAN interface; I am still seeing a lot of the [TCP segment of a reassembled PDU] traffic items in wireshark. 

BTW, I have a Windows XP machine in the house which is functioning fine on the same wireless network.

Edit: to answer your question, the extra ARP request is sent by the router to my computer about the same time that things fail... so could be just circumstantial, but it seems to be related.

Cheers,

David

---

### Post by caljohnsmith on 2008-08-05
> **iago1983 said:**
> 
arp -s 192.168.1.1 00:11:22:33:44:55 

David, I looked through your Wireshark log, and I think you made a mistake when you assigned your router the above MAC address. According to your wireshark log, I believe it should be: 
```
00:0c:e3:63:9b:20
```
Just click on any packet in that wireshark log you posted that has a source of 192.168.1.1, and if you look under the Ethernet II section you will see the source MAC address as 00:0c:e3:63:9b:20.

How do you have you router WLAN configured? I would try to set it basically back to defaults just to see if there are any issues with any settings you may have changed with the router. Now I know you said the WLAN works fine with your Windows XP computer, but sometimes Network Manager in Ubuntu can have quirks, and we want to remove as many variables as possible here. In other words, make sure encryption is off, set MTU back to auto, etc. 

Are there any other strong WLAN networks in the area that are on the same channel as you? You've probably all ready checked that, but try to use a channel as far different as possible from any other strong networks.

Anyway, just some ideas, let me know how it goes. :)

---

### Post by iago1983 on 2008-08-05
Sorry, the 00:11:22:33:44:55 was just an example :) I know what the MAC address of the router is and used that initially. Thinking about it though, looking at the capture, it's the router that would need the static ARP mapping, not my PC.

I'll try a different clean WLAN today and see how that goes; I'll also revert my settings on my WLAN to basics and see if that makes a difference.

Thanks :)

David

---

