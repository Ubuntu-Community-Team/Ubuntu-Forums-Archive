---
title: "Connecting With Mac?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by zlegge on 2007-03-12
I'm using Kubuntu Edgy Eft and I'm connected to the Internet via wireless adapter through a gateway to a PC.  I have a mac that my brother wants to use, if I just ran an Ethernet cord from my computer to his.  Would it be connected, would it connect to the Internet?

---

### Post by ubix on 2007-03-12
If you used coax cable connection this would work. However, I'm almost certain you  have a so called twisted pair cable with connectors similar to telephone connectors, only a tinny bit larger. If I am right about that, you'll need to buy what is called a **"5 port 10/100Mbps Ethernet Switch"** and connect Ubuntu and your brother's Mac via this switch. Therefor, your Ubuntu should have two NICs (network cards) one for your wireless and the other to connect via the switch to the Mac. If you do not have such a configuration you will probably need to arrange for one like this. Before you confirm the above or tell us what is it you have, it is pointless to continue. For instance, you'll need to set up two local networks for this to work, and yes it should be possible for both of you to surf and otherwise use the net.

---

### Post by zlegge on 2007-03-12
What is a twisted pair cable?  And what is a coax cable?  and when you say 5 ports, is that like a modem? Or just a name for a cord?  Thank you for helping me! :) 


By the way, my laptop and my brothers mac both have Ethernet cards if that helps anything.  Also I was thinking, if I can connect an Ethernet port on both of them, wont the computer think that im now connected via Ethernet and try to get the Internet from there?

---

### Post by ubix on 2007-03-12
Ethernet switch is a connection box through which you connect as many computers as there are ports on it in a single network. Your Ubuntu and your brother's Apple should be connect via such a box.  However your Ubuntu is at the same time connected to the outside world on a different network. Each NIC (network card) represents an entry point into a (usually different) network. Such will certainly be your case when you connect all the stuff together. 

Here is an example for an Ethernet switch: ( [5-Port-Ethernet-Switch @ Amazon]("http://www.amazon.com/Netgear-FS105-5-Port-Ethernet-Switch/dp/B00002EQCW") ). Indeed it looks like a modem or a router but is distinctly neither of the two.

The following are the examples of the two type of cables. 
[http://en.wikipedia.org/wiki/RJ-45](http://en.wikipedia.org/wiki/RJ-45)

Of course they require different type of NICs. You can tell what you have by looking at the connectors on the boards and your cables. They should resemble the telephony connectors. Cables that look like telephone cables only a bit thicker, are "twisted pair" cables. Their connectors are called **RJ-45** connectors:

The following are coaxial (coax) cables, with rounded barrel like connectors with a sort of a needle in the middle.
[http://en.wikipedia.org/wiki/BNC_connector](http://en.wikipedia.org/wiki/BNC_connector)
The connectors for coax cables are called **BNC (bayonet connectors)**.

Your NICs, through which you wish to connect your Ubuntu and the Apple, must ce equipped with female **RJ-45** connectors.

---

### Post by zlegge on 2007-03-12
First of all I just wanna say thanks again for going out of your way and helping me.  

So basically I'm gonna need a Ethernet Switch and RJ-45 connectors to connect the two computers.  How would I set it up on Ubuntu to make it so it will connect through the adapter and also give information to the Ethernet port?

---

### Post by ubix on 2007-03-12
There are a couple of issues here, to be taken into consideration, which may effect the way you should design your network. In my earlier suggestion I assumed you need a functioning connection between your brothers Apple and your Ubuntu, perhaps to exchange files between them locally. Also your mixing and matching different connection types, namely wireless and wired, makes my earlier suggestion a reasonable choice. This solution requires that we turn your Ubuntu into a "router/desktop" which may not be worth while, or perhaps too demanding for the effect you'll get with all this reconfiguring. Perhaps you'll even need to rebuilt your kernel in order to enable routing.   However, if all you need to do is, to connect both machines to the Internet, you may have a much simpler solution, with a router, which is just like a switch, and roughly at the same price range, and which will require that your brother gets a wireless NIC, or that you replace your wireless NIC with a regular one, containing a RJ-45 connection. An even better solution would be a "combo router" that can connect wireless and wired computers, but such a product may not be available at a reasonable price.

And, no you can't have just **RJ-45** connectors by themselves, they are built in features into NICs, and they come with cables, you buy to connect networking hardware. Therefor unless, you plan to build your cables yourself, you most likely will never have a need to deal with **RJ-45** connectors by themselves.

Talking about or even setting computers before you have a clear picture of how exactly you want to connect them is prematurely. Indeed, how would you make a decision about the design of your network if you do not know exactly what are the building blocks. Expect a lot more questions here, before we'll come closer to a satisfactory answer.

---

### Post by zlegge on 2007-03-12
Okay, but what are NICs? and what does it stand for?  When you said replace my wireless NIC to a regular one, what did u mean by that?  Or even get a wireless NIC?  Because yes, all I need to do is connect both of them to the internet using my connection as you know through my wireless adapter.  But really what I need to know before we go on is a Wireless NIC is or what even a NIC is besides for the wireless part?

---

### Post by ubix on 2007-03-12
**NIC** is the abbreviation for "[COLOR="Red"]**N**[/COLOR]etwork [COLOR="Red"]**I**[/COLOR]terface (adapter) [COLOR="Red"]**C**[/COLOR]ard". Most modern motherboards today come with a built-in network adapter, so a **NIC** in this case is a bit of a misnomer. Unless your computer has a built in wireless network adapter, you can tell whether your computer has any kind of networking hardware by looking at the back of your computer, if there is a connector suitable for the network cable (today most likely an **RJ-45** female). Things get more complicated if network hardware is connected to your computer via USB ports.

To cover all the possibilities of what is and how does a NIC look like I am not interested in explaining. Perhaps someone else will kick in. But if the above explanations are sufficient for your understanding, you should first tell us:[list] [*] What kind of NICs and connectors you have on your two computers?
[*] How is your wireless adapter connected to the Internet?
[*] Is your wireless adapter a router, i.e. can it listen to multiple computers or just to one. Perhaps it would help, if you tell us its brand, and product name so its technical specs could be looked at.[/list]

---

### Post by zlegge on 2007-03-13
My brothers mac has a ethernet card as an NIC and can only be networked that way because it dosen't have an airport card for wireless capabilities.  What do you mean by how my wireless adapter is connected to the internet?  It IS connected to a PC wirelessly, the PC has a connection to the internet by a modem that is both wireless and ethernet.   The wireless adapter I have is not a router, but the router that it is connecting too can listen to multiple computers.  The brand name is DLink, model: DI-624.  But the mac wouldn't be able to connect with that, unless I ran an RJ-45 cord all the way too it, but that's on differnet floor levels.   Basically what were asking ourselves here is can I add to my network by using the RJ-45 cords from my laptop to the Mac and be able for the mac to understand that it is using my network interface to connect to the internet.

---

### Post by ubix on 2007-03-13
No, as much as I understand you, can not connect your laptop and your brother's Apple directly with a single wire. You'll need two wires and a hub or a switch to connect them. But by far the best solution would be to connect the Apple wirelessly to the DI-624 router. Providing there is a spare USB port on your Mack, you should buy a Wireless USB adapter, for instance [D-Link's DWL-G122]("http://www.dlink.com/products/?pid=334").

If this is not possible then you'd have to buy an Ethernet switch and connect the Laptop and your Mack through it. This will require your laptop to act as a router, passing data from and to your brother through the laptop to the DI-624 router upstairs. I do not think you really want to go through all the trouble to set this up, unless you have time to spare and are willing to learn. A laptop is a moving thing and is usually not used as a router unless you inspire to walk around and route local data that happen to be at the time in your vicinity to some data gathering facility.[-X

---

### Post by zlegge on 2007-03-13
OKay thank you, I understand everything now.  I'm eventually just going to buy a airport router and get an airport card for the mac.  So the PCs and the Macs can all be connected wirelessly without any hassle.  Thanks for the help!  but basically what your telling me is that it's not worth the effort to go through all that not being wireless and have downsides.  For ex. the not being able to carry my laptop around.  

Thanks again! :-P

---

### Post by ubix on 2007-03-13
Wait a minute, we still did not understand each other well enough. Particularly, why are you going to  buy an "airport router". All you need is a wireless USB adapter to be plugged into your Mack. It should talk to the existing DI-624 router you already have upstairs, or is this not possible? :confused:

---

### Post by zlegge on 2007-03-13
It's not possible because the Mac does not have wireless capapbiltiies.  You know how some laptops have 802.1g/ wireless built in so it can use the information given by wireless adapters?  Well, the mac does not have that, so it would need an airport card built in, plus the macs aren't compatible with my wireless router.

---

### Post by ubix on 2007-03-13
I do not completely understand these issues, and  do not particularly care about wireless. I know that many things do not work as they should. Linux used to be ahead of everybody else in this area, but lately things have turned around and it will take a while before sound reasoning and standards will prevail. Anyway, thank you for the enlightenment.  8-)

---

### Post by zlegge on 2007-03-14
Your Welcome, I'm glad we had this conversation.  I learned a lot!! :)

---

