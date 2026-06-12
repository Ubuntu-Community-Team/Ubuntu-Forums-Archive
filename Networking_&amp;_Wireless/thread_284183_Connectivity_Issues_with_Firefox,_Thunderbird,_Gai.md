---
title: "Connectivity Issues with Firefox, Thunderbird, Gaim"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by lukeflatman on 2006-10-25
Just the other day i was connected to a new broadband service who furnished me with a new broadband router. I *think* although i'm not entirely sure that the internet was working fine at this stage. (i say think as i dual boot with windows to use Cubase a lot).

Just the other day I update my distr and it downloads 20 or so new updates. and then i reboot. At this stage the Network connection breaks.

I had network manager installed and it said everything was fine and dandy. I could still use synaptic package manager and the like. However Firefox, Thunderbird, and Gaim all would basicaly sit there and do nothing upon trying to connect/browse/download messages.

I read through a load of posts and sussed out a few people that had similar problems and figured that it must be my new router not handling IPV6 properly. so I go through various suggested things to disable IPV6 (the about:config in Firefox, the aliases file in modprobe.d and I also blacklist the IPV6 module).

The situation NOW is that firefox will browse but only after spending 20 seconds or so hanging when trying to load the first page i go to. Thunderbird seems to be ok, although again INCREDIBLY slow. Gaim however, won't connect at all, i've tried using 'http method', nothing works.

I hate network problems because they're the one thing linux is supposed to be absolutely flawless in handling! mmmhmmm

anyways, i'd be really greatful if anyone could help me with this i'm completely stumped!!!

Many Thanks

Luke

---

### Post by Rhubarb on 2006-10-25
I don't know that much about networking, but:
* Try to see if it works ok from the live cd.
* I've had awful problems with all sorts of routers in the past:
     D-Link
     Belkin
     Netopia
     Netgear
     Linksys
     Billion

So it might pay to check the router manufacturer's website for the latest firmware.

The only other way would be to try a different router / try a different internet connection - say at your neighbours' place or somewhere.

Hope you figure it out without pulling too much hair out :-k

---

### Post by lukeflatman on 2006-10-25
hmm, good call.

Unfortunately due to some wierd glitch i can't test the Dapper live CD as my computer won't boot from it. It always hangs at the 'Mounting Filesystems' part. I could try with an older version though, dunno if it would really help with any conclusions though.

I checked the specs for the router (it's a *Solwise SAR-600E*) and it didn't mention ipv6 at all. I then checked the technical fora and some people said the ipv6 support was shakey at the very best. However there has been a reasonable few firmware upgrades since mine was built. Perhaps the new one will work, I very much doubt it though!

This in mind, is there anyway of completely nuking ipv6 on Ubuntu? i've tried the usual things as detailed above.

Pies

Luke

---

### Post by Rhubarb on 2006-10-31
I wouldn't have a clue how to remove ipv6 from ubuntu.
All I can recommend is to try the firmware updates for your router.

---

### Post by stream303 on 2006-11-13
I'd doublecheck your /etc/resolv.conf file and see if any of your ISP's dns server addresses are there.  If not, try placing the primary and backup isp dns server addresses in your router setup page.

OR you could manually force it with a quick edit:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

lets see how this goes

---

