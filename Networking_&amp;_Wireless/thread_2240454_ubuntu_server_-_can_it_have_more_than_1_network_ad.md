---
title: "ubuntu server - can it have more than 1 network adapter?"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by dave131 on 2014-08-20
I hope to building a cheap server soon for 2 purposes (1) *try* learn server - that may be too difficult for me (2) install something (mediatomb has been suggested) so I can keep movies, music, pictures, etc., in 1 place but have multiple devices (TV's, tablets, etc.) accessing those things sometimes simultaneously.  I can only use wireless at this time (it seems fast enough when letting my tablet's xbmc app access media in xbmc on a Raspberry Pi), but if I want more than 1 device to potentially be accessing this at the same time, am I better off having more than 1 wireless adapter on the server?  Is it even possible to have more than 1 wireless adapter on the same box connected to the same wireless network?

I know this is probably a dumb question, but I'm a newbie and really don't know anything about this.

---

### Post by nix_weasel on 2014-08-20
unfortunately with network devices wired and wireless (except in advanced cases with a lot of extra configuration) its not possible to have them both connected to the same physical network at the same time "right out of the box" so to speak so simply adding another wireless card to try and double your speed by having two wifi connections wouldnt work.

but you can do some neat things with linux for example my fileserver box has two wireless cards one for connecting to internet router the other is set up as a wireless access point for boosting the wifi signal in a dead zone meaning my wireless devices connect via my fileserver that gets a better wifi signal to the internet router i would be glad to help you set something like that up

---

### Post by dave131 on 2014-08-20
Thanks for the reply.  I'll keep that in mind when I get my server built up.  That will probably be a little while.

---

