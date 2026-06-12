---
title: "Help with WRT54GL - can't access router"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by dianep on 2007-10-10
Hi there,

I'm trying to set up a wireless network at home using a WRT54GL router.  I don't yet have
access to the internet from home (writing this from work) but I thought I would set up the
router.  To set it up, I connected my desktop (running ubuntu feisty) to the router with an
internet cable (didn't want to accidentally connect to someone else's router) and then set 
things up like so:

Connected to 192.168.1.1 using Firefox. Asked me for password and I got through.
Set up router name and wireless network name (not the same name though).
Set new password for the router so only I can access it.
Set up WEP with passphrase encoded. Choose the first encoding (1-4 were given).
Router is using Firmware v4.30.7 and I didn't change any of it.

Okay, so now I try to reconnect to the router over wireless.  I can ping the router, no
problem, but I can't get the ip address 192.168.1.1 (keep getting the standard Firefox
message for unreachable address).  So I figure that perhaps my wireless card in my
Dell computer is screwed up and needs configuring, or whatever.  So I try to reconnect
to the router using the internet cable again.  I still get the standard Firefox message for 
unreachable address.

Can anyone tell me whats going on? Is there some way to reset the router and start
again?  It seemed to be working before.
Thanks
diane

---

### Post by kevdog on 2007-10-10
Reset the router -- I bought a 54gl and to tell you the truth had to resort to setting it up from windows with IE.  I know firefox had issues aways back and am not sure if these have been resolved.

Ok since you are still reading the thread can you still connect through a wired connection to the router?

If yes, forget the hard reset.

Please tell us more about wireless setup -- and you must bring wired interface down and bring wireless interface up.

lshw -C network
lspci -nn
iwlist scan

---

### Post by dianep on 2007-10-10
Thanks.  I'll give this a go, but it might take me a couple of days to get back to it
(my home computer is now off limits while my floors are fixed).
Thanks again,
diane

---

