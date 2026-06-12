---
title: "bridge pstn to ethernet via computer for voip?"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by piusvelte on 2008-04-05
I tried to fit as much information into my confusing title as possible. Also, I've searched here and generally through google, but if this has been discussed already, then I apologize for the dup.

OK, I'm looking into setting up voip and have a question about something that seems possible but I can't seem to find anyone doing it. Can a computer with both a dialup modem and ethernet nic be setup to bridge pstn to ethernet and serve voip to a regular pstn phone? Does that make any sense? Network connections can be bridged and computers can use voip. It just seems that I could dedicate a 'voip server' and serve the whole house. I already have all the hardware, so this would be a no-cost implementation, which fits right into my budget! :)

Any help or suggestions would be great. Thank you!

---

### Post by piusvelte on 2008-04-06
It looks like asterisk.org will do what I'm looking to accomplish. I'll research that some more. Does anyone have any experience with asterisk or similar product for setting up a gateway for pstn to ip? 
Thank!

---

### Post by Robstarusa on 2008-04-08
> **piusvelte said:**
> It looks like asterisk.org will do what I'm looking to accomplish. I'll research that some more. Does anyone have any experience with asterisk or similar product for setting up a gateway for pstn to ip? 
Thank!

I use asterisk regularly.  What questions do you have ?

You should check out the digium cards with FXO interfaces to bridge to PTSN.

---

### Post by piusvelte on 2008-04-28
> **Robstarusa said:**
> I use asterisk regularly.  What questions do you have ?

You should check out the digium cards with FXO interfaces to bridge to PTSN.

Robstarusa,

I'd love some help trying out voip, using asterisk as a pstn<->ip gateway, though I'm sort of tied up with hardy upgrade problems. I have a x100p modem, I think, for which I was able to install the fxo driver for asterisk, so I think I'm on my way. A co-worker commented that I'd need to find a way to get my pots phones to ring when a call comes through the asterisk server. Do you know anything about that? He said I'd need a 90v source for the ringer, which doesn't sound right, but otherwise I could do what I want, but I'd never know when a call came in. Thank you!

---

