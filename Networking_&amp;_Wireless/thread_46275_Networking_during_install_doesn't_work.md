---
title: "Networking during install doesn't work"
date: 2005-07-04
forum: Networking &amp; Wireless
---

### Post by stephanhughson on 2005-07-04
Hello,

This is my first post, I'm glad this distribution has a forum!


I am trying to install Ubuntu. Unfortunately, my network isn't quite working yet.

Here is what I have:

192.168.7.1 - router
192.168.7.2 - wireless access point
192.168.7.3 - this computer (which is going to get ubuntuoed!) \\:D/ 

The network is not running DHCP. The computer has a normal ethernet card, based on the Realtek 8139 chipset. I think that's the number, it's the one that everyone has basically, just the normal standard one.

This computer has had Debian on it, and that worked, also Windows... :? but the fact that Debian was ok confuses me.

So, I get to the point in the installation where it asks me for my settings. I enter them manually, because my DHCP is off. I have tried switching DHCP on, but it didn't work either, not sure why, but manually should be ok.

Then it goes on to the bit about partitioning my drive. At this point, I press Ctrl+Alt+F(1?) to go on to a spare console.

The network should be up at this stage, so I try:

wget [http://192.168.7.8](http://192.168.7.8) (a server on my network)
doesn't work

wget [http://www.something.com](http://www.something.com)
doesn't work

ifconfig -a :

eth0
Link encap: Ethernet HWaddr: 00:E0:etc.
inet addr: 192.168.7.3 Bcast:192.168.7.255 Mask: 255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
RX packets:0 Errors: 0 dropped: 0 overruns:0 frame:0
TX packets:0 errors: 0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelength: 1000
RX bytes: 0 TX bytes:0
Interrupt: 10 Base Address: 0xac00



route -n:

Kernel IP routing table
Destination, Gateway, Genmask, Flags, Metric, Ref, Use, Iface

192.168.7.0, 0.0.0.0, 255.255.255.0, U, 0, 0, 0, 0, eth0
0.0.0.0, 192.168.7.1, 0,0,0,0, UG, 0, 0, 0, eth0


This all seems fine, so I don't know what the problem is. It's driving me mad ](*,) 


Last but not least, here is my /etc/network/interfaces

iface eth0 inet static
address 192.168.7.3
netmark 255.255.255.0
network 192.168.7.0
broadcast 192.168.7.255
gateway 192.168.7.1
#dns-* options are implemented by the resolvconf package if installed
dns-nameservers 192.168.7.1


(192.168.7.1 is my router, which has a DNS forwarding thing to my ISP)


It works in Debian, I have no idea why it won't work this time, I am entering exactly the same settings, I don't have a wierd network card, if anyone has any ideas, I would be very grateful to hear them.

Remember though, this is when I have opened another console during the installation, however, I can't see why this wouldn't work. I have also let it run right through the installation, deleting my current OS once before, only to find out that I had no network support once it had finished, this time I am not doing that again!

I hope someone can help me.

Thanks

---

### Post by stephanhughson on 2005-07-05
Any ideas?

Please!

---

### Post by poptones on 2005-07-05
I understand your frustration. I also have had the experience of leaving messages that seem to go forever without a response. Unfortunately all I can offer is sympathy, I do not know how to fix your problem. 

But I will offer this suggestion: if you look around you will find "geeks for hire." Yes, I am actually suggesting you pay for a solution. Even more than that, I'm suggesting you follow up your resolution here so we can all share in it. I've done this myself, actually I find it kind of rewarding to be helping out someone else in the community - and all it cost was the income from a couple of CD sales on ebay.

Here's the best I can offer: there's a bug in the installer in hoary, it will "hang" at one point if the network is plugged in. Have you tried installing it without the network cable plugged in at all? When it finishes like this it will not have a network configured - you then need to open the network control panel and configure it yourself (there is a wizard) and then click the "enable" box. Did you try this yet?

---

### Post by stephanhughson on 2005-07-05
No, I haven't tried that, maybe I should.

Sorry for bringing this topic back up to the top, I know it's quite cheeky!


I think I will just bit the bullet, install it, erase my current OS, then sort out out the network later. I have all the setup details, I think....

If I reply to this topic, then it worked!

---

