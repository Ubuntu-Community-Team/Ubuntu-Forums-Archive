---
title: "unbuntu as a WRT54G replacement"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by jumpslu7 on 2008-06-30
I've got a mini ITX machine on which I've got ubuntu hardy server edtion installed.

I use it as for web/database/file server purposes.

I'd also like to turn it into a wireless access point so I can ditch my linksys router WRT54G.

Can anyone recommend any firewall config utils with a web frontend that I could install?

Remember, I've got server edition installed, so the desktop applications are out.

I've got an edimax 802.11n card installed, ([http://www.edimax.com/en/produce_detail.php?pl1_id=1&pl2_id=44&pl3_id=126&pd_id=225](http://www.edimax.com/en/produce_detail.php?pl1_id=1&pl2_id=44&pl3_id=126&pd_id=225))  although I've been unsuccessful in setting the card into master mode (to use the box as an access point).

Can anyone tell me if the card is capable of master mode - I'm using ndiswrapper with the rt2860 drivers that I'd snarfed from the windows install.  the card's manual says its capable, but mentions accessing "soft" AP mode only through the windows software interface.

I'd also like to monitor traffic flowing thru the box.  I'm interested in throughput, and would like to know whats available.

I used to use MRTG on a previous ubuntu installation, but I'm wondering if there are any alternatives?

Specifically, I'd like to see traffic breakdown by packet type - (EG how much traffic via outbound connections to port 80 etc)

cheers,
[http://belfastgeek.net](http://belfastgeek.net)

---

### Post by ilrudie on 2008-07-01
WRT54G is solid.  Drop dd-wrt on it and keep using it.  That would be my advice.

---

### Post by jumpslu7 on 2008-07-03
There are a couple of reasons why that's not a suitable/possible situation.  

Among other features, I want to traffic accounting through the router, and WRT54g is useless at that; 

And since I've now installed the WRT54g at a relatives home, its not possible!!!

Since this is an ubuntu forum I'd really appreciate an ubuntu solution!!!  Hasn't anyone setup an ubuntu box as a router that could help?!

cheers,

---

### Post by kevdog on 2008-07-03
I second the opinion of dropping ddwrt on the wrt54g router.  I know what you want to do is possible, but the ddwrt software is awesome.  I would find it very difficult to reproduce its functionality alone with an ubuntu-rigged equivalent.

---

### Post by jumpslu7 on 2008-07-03
yeah, so I just gave the WRT54g to a relative so that's not possible.

---

### Post by ilrudie on 2008-07-04
> **jumpslu7 said:**
> yeah, so I just gave the WRT54g to a relative so that's not possible.
Ok.  So you will need to find a solution or buy another wireless router.  I get that you would prefer to find a solution but here is some food for thought:
You came to Ubuntu Forums looking for an Ubuntu solution to your problem but consider walking into a Ferarri dealership and asking for tractor.  The dealer could be real nice and try to hook up some plowing equipment to a sports car but it might not end up being the best tractor you could have gotten even if it can do 0-60 in under 5 seconds.  Similarly, Ubuntu may not be the best choice for building a wireless router.  Ubuntu is a great desktop OS.  It has some very new packages and gets updates nearly every day and that's not really ideal or necissary for a wireless appliance.  It's also fairly heavy for running an appliance.  Do you need bluetooth or a waccom tablet for a router?  Granted you can turn off and remove the heavyness but then you just stripped out what the Ubuntu devs worked hard to put in.  I'm sure there is a good Linux distro out there for doing this (after all dd-wrt is linux based) but I really can't think of what it is.  Some of my friends from work have built routers/loggers/firewalls and similar devices (none of them wireless) on netBSD.  That might also be a good place to look.  Good luck.

---

### Post by jumpslu7 on 2008-07-04
Here I know that Ubuntu is a decent desktop linux distro, but as previously stated, installed ubuntu server.

I wanted my existing Ubuntu installation to double up as a wireless access point.  I must admit I'm surprised at getting negative comments instead of help!  

I'm not looking for the best solution, or one thats popular, I'm looking for one that fits my existing hardware; a more energy efficient solution should be on everyone's list, and adding extra unnecessary devices to a home network is just going to add to an energy bill!

I found nocatauth, and while it looks a bit old (last build in 2004), it seems to be well documented and usable for providing user authentication to the access point.

nagios looks like it could help with traffic accounting and I found on the edimax wireless card website that they've got linux drivers for the card that might help get the card into master mode to serve as an access point.

I'll also need a firewall and NAT; and I'd like to keep wireless users completely seperate from the rest of my LAN.

[this post]("http://ubuntuforums.org/showthread.php?t=376283") should help with all that.

I'd be interested in hearing advice and tips from people with experience in what I'm attempting (instead of opinions from folks who haven't tried - and think I shouldn't!!!)

ta!
[belfastgeek]("http://belfastgeek.net")

---

### Post by ilrudie on 2008-07-06
I'm sorry that you are disappointed with the responses you have gotten.  Although it may seam like no one is trying to help I assure you we are.  I have never done what you are trying to do but if you are dead set in doing it I can give you some advice on how you might want to setup and run the OSs.  Since you are trying to run two very different things on 1 physical piece of hardware I would recommend looking into VMs.  Most open source OSs will have good support for the xen hypervisor.  I would recommend running two seperate paravirtualized machines.  A paravirtualized machine essentially means that the kernel is xen aware.  This will give you fairly good performance and the advantage of being able to keep the router up while you are rebooting the server.  This will also allow you to take snapshots of the router before making changes so if you break it or destroy it you can easily start over from the last working state.  It also means that when you destroy the router it won't affect all the work you have done on the server and vice versa.  I have heard that some vms and wireless do not mix well so you may want to do some research or ask if anyone has experience with xen and the wireless card you are thinking of getting.  Since it looks like power saving may be one of your motivations running under xen will allow you to shutdown the server when its not needed and if your CPU has good stepping save some power without shutting down your router.

The other advantage that xen would give you is the ability to run Ubuntu for your server and still experiment with other linux or BSD distrobutions that may be better suited for your goals if you choose to.

As far as firewalls go iptables is standard and probably one of the best.  It may have a steaper learning curve than some of the others but once you get it set up the way you want it you should see very good stability from it.

iptables is also capable of doing NAT for you but I have not set it up.  I'm sure people on the forums have done it so you can ask about that specifically and probably get more responses.  It looks like you have already found a thread about this and its probably a good starting place for you.  Most good routers and firewalls these days probably use iptables or ipchains.

Good luck.

---

### Post by fixture on 2008-07-06
hi, specifically regarding the wireless ap issue. I have been turning laptops into APs for a while. The short answer for whether the Edimax can turn your machine into an AP is No. This is because typically master mode code resides in native linux drivers. Currently you are using windows NDIS driver in linux. There are two Ralink projects, an open source one that supports master mode to a certain extent but only on older hardware, and a closed-source project sponsored by the company that seem to have the potential for future master mode support. 

Also, more bad news for you, just like you, I have been looking to turn N cards and laptops into N wireless APs, 1) N does not seem to perform better than G, 2) currently there is no master mode capable linux driver

---

### Post by fixture on 2008-07-06
In addition, G performs pretty damn fast, and the most mature master mode driver is the Madwifi driver.

---

### Post by fixture on 2008-07-06
lastly, the best linux distro for routing seems to be ClarkConnect, though the distro it is based-on is ancient (FC4 I think), and it may be a pain in the *** to add functionalities other than its native modules (which are awesome)

---

