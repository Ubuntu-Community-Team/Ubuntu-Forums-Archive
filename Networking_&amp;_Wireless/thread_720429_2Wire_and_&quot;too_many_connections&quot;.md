---
title: "2Wire and &quot;too many connections&quot;"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by sullivan.t on 2008-03-10
I have a 2Wire dsl modem/router/wireless device, model: 2701HG-B and am currently running Ubunu Gutsy.  I love it; the ubuntu party.

Recently, we decided to switch from cable to DSL; it's cheaper and we don't watch tv.  Anyway, the cable setup worked perfectly through my linksys router to the cable modem.

With the 2wire, it would seem that my linux machine causes the router to reboot when I try to download a lot of data.  Not torrents, but simply the latest edubuntu iso, or while playing WoW via Wine.

My wife's windows machine is just fine, and so is the kids machine.

Do we have any thoughts on this?  Why would it be different between Ubuntu and Windows?

I've done some searching and tried a few things:

-Setting up the linksys I used on cable as the WAP and putting the DSL modem into bridging mode.  -- Still reboots.

-Turning down the speed to B, from G -- Still reboots.

-Tried, in the mdc, to turn off all of the firewall freakouts and it still reboots.

What's next?

I do have a support ticket open with AT&T and they are shipping me a replacement router sometime this week - that's my only "real" attempt at fixing this.    Everything else is just config and software.

---

### Post by lloyd_b on 2008-03-10
Hmmm - that is weird.  Am I correct in assuming that you've tried the large file downloads and such from one of the Windoze boxes and it works?

One (unlikely) possibility: what is your "MTU" set to? (In a terminal window, "ifconfig", and look for the "MTU:" entry).  I've *never* heard of of an MTU issue causing a router to reboot (usually it just won't let you reach certain sites), but it's one place where Win and Linux *can* have divergent values.

To test this possibility, in a terminal window "sudo ifconfig eth0 mtu ####" (assuming you're connecting via eth0).  The "standard" value for MTU is 1500, but try reducing it by 100 at a time until you get down to 800 or so (if the problem still persists with MTU set that low, then MTU isn't the problem). 

FYI: Those 2wire units are pretty common (I have a 2700HG-D), and I haven't heard of any conflicts between them and Linux (mine works like a charm, even though I run P2P software as well as large downloads from my 'buntu boxes).

Lloyd B.

---

### Post by sullivan.t on 2008-03-10
You are correct in assuming such - I've played world of warcraft from the windows boxes and it works just fine.  Though I haven't gone so far as downloading the same iso from a windows box...

I'll try dropping the MTU and see where that gets me - I'm on hold with 2wire at the moment, and that gives me plenty of "free time" to try new things...

---

### Post by sullivan.t on 2008-03-10
Yeah, in the last hour or so I've noticed it reboot twice - and once while I wasn't even powered up.

---

