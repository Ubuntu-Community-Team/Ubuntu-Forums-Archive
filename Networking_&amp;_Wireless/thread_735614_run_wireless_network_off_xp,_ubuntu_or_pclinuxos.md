---
title: "run wireless network off xp, ubuntu or pclinuxos"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by Raccoon1400 on 2008-03-25
I wan to set up a wireless network that is broadcasted by by desktop running xp and pclinuxos (network can be set up in either, whatever works first) and picked up by the broadcom card in my ubuntu laptop.

I also want to set the laptop to broadcast to the desktop.(there is only one network cable in the room.)

The computer that broadcasts will be hooked up to a wired network.

Any suggestions? I tried a couple things, but am not quite sure how to do this.

---

### Post by Eiríkr on 2008-03-26
Buying a cheap wireless router is a better bet, in terms of security, convenience, scalability, etc.  This is what I've got, with two wired computers, a wired network printer, and two wireless laptops all sharing one DSL connection.  

A simple wireless router costs just in the $30-$70 range.  Daisy-chaining computers to share network access works, but it's cludgy, and means that the computers closer to the network cable have to be turned on for computers further down the chain to get access.  A router isn't that expensive, and allows for a parallel networking setup, so it won't matter if your desktop is turned off, or bluescreened, or in the shop, as you'll still be able to connect with your laptop.  

Cheers,

Eiríkr

---

### Post by Raccoon1400 on 2008-03-26
I'd still rather have the laptop able to connect through the desktop. Most of the time I would have the laptop hooked up directly, but I want the option of connecting both at the same time.

---

### Post by Eiríkr on 2008-03-26
A router would give you the option of having both (or more) connected at the same time...  :confused:

Out of curiosity, do you have any specific reason for having your laptop connect via your desktop?

Cheers,

Eiríkr

---

### Post by Raccoon1400 on 2008-03-26
The laptop is my main computer. I use the desktop mainly for media, and sometimes I want it online. Hosting a network of the desktop would give me more flexibility for where to use the laptop, though most of the time I would connect the laptop to the wired network (our house has a router and a wired network). I want to do this without buying more hardware.

---

### Post by Eiríkr on 2008-03-26
> I want to do this without buying more hardware.

Fair enough.  But note that, if you don't already have a wireless card for your desktop, you'll need to buy at least that.  At which point, it makes some sense to pay for a router, which might only run you an extra $10 more than the wireless NIC...

> Hosting a network of the desktop would give me more flexibility for where to use the laptop

Simply setting up a wireless network of any sort should give you more locational flexibility.  But routing through the desktop does potentially hamstring your wireless capabilities if you ever need to take the desktop offline.  You'll also need to get into the nitty gritty of setting up routing on your own (nothing too terrible, but prone to its own fun issues), whereas a router comes preconfigured to do exactly that.  Just something to think about.  

Cheers,

Eiríkr

---

### Post by Raccoon1400 on 2008-03-26
The desktop does have a wireless card. I plugged a spare one into the motherboard yesterday. 
The laptop will probably be wired to the main network most of the time anyways. If I want to use it somewhere else, I will turn on the desktop and plug it into the network. This would also be useful if I need the desktop online, like to find track info for media files.

---

### Post by Eiríkr on 2008-03-26
Sounds good.  Now that I understand your hardware parameters better, I think [this online guide]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html") might be what you're looking for.  Hope it helps.  

Cheers,

Eiríkr

---

### Post by Raccoon1400 on 2008-03-26
Thanks. Running the network off linux on the desktop might be more secure anyways. If this doesn't work with pclinuxos, I will install ubuntu on it as well as the laptop when hardy comes out.

---

### Post by Eiríkr on 2008-04-09
Well, theoretically, your could get this setup if you follow the linked guide to set up one wired / wireless laptop as the router, with that one wired into the internet connection, and have all the other laptops connect to the router laptop via wireless.  I've never done so myself, and the only laptop I have is a Mac (and I'm not messing with it for any dual boot setup :)), but that would seem to be the way to go.  

Cheers,

Eiríkr

---

