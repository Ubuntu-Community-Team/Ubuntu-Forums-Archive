---
title: "Hooking up to network via (wireless)laptop's socket"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by halfconscious on 2007-06-11
Hi people, maybe someone out there can help me
I've connected a mini ITX box to my laptop's ethernet socket (eth1). The laptop
is connected to the net via wireless (eth0). 
My problem is I can't see the net (or wireless router) from the mini ITX box, I can
only see the laptop. 
Thanks 
Steve

---

### Post by halfconscious on 2007-06-12
Is this difficult? I thought this would be totally routine.

I've tried setting the laptop as a gateway/default route on the ITX box. 
I just need to get the laptop to route packets between it's ethernet ports.
I've tried brctl - following the HOWTO's/docs I can find ... and beginning
to think some of the warnings about expecting probs with wireless 
adaptors might be applying to me.
brctl sounds good, as I can keep the IP address of the ITX box static whether
I want to plug it directly into the router OR into the laptop - but after several days
of trying I still can't get it to work.

At this stage I really don't care if I have to put the ITX box on a different subnet
when connected to the laptop. 
Do I need to use IPTABLES to get Linux to transfer packets between I/Fs?

( If anyone is wondering why I'm messing around connecting to the ether socket of
a laptop when I could connect directly to the router - my router is in another room
with a desktop system nearby - I nicked the desktop's monitor/keyb etc to get 
Feisty installed on the ITX box .. but now I want to sit in my living room and
start encoding all my CDs on the ITX box while watching TV, and just want the
laptop to shell onto it as it is headless .  I had this working about a week ago..
and was happy until I realised I didn't have some packages I needed on the
mini-ITX ... that's when I realised it couldn't see the net - when apt-get wouldn't
work.
I could/should? have just powered it down and carried it next door to hook it directly
into the router, and saved my last few evenings! But now I have got hooked into 
trying to get it working as it is... because surely this is trivial if you know what
you are doing. Anybody? Please?).

---

### Post by Sendervictorius on 2007-06-12
Yes it is easy. You need to set up your PC to perform Network Address Translation (NAT)

Best / quickest option without getting into the insides of IPTABLES is to install firestarter from synaptic.

Then start up firestarter and follow the install wizard. 
Just follow  the instructions: set eth0 on the "Network Device setup" page, and set DHCP or fixed IP address as appropriate.

Then, on the "Internet Connection Sharing" page of the wizard set "Enable Internet Connection Sharing", and choose eth1 as your local network device. You probably also want to enable DHCP if you want to automatically assign an IP address to your mini ITX box. Otherwise just choose a fixed IP address.

It's that easy.

---

### Post by halfconscious on 2007-06-12
Keep talking like that! That's what I want to hear :0) 
I'll try it out as soon as I get out of this office and back home. 
Many thanks!

---

### Post by halfconscious on 2007-06-12
You're right. That was easy. Thanks!

---

