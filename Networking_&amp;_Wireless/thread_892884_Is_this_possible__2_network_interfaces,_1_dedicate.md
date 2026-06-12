---
title: "Is this possible:  2 network interfaces, 1 dedicated to Firefox?"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by databarn on 2008-08-17
Currently I have a 10/100 Mb Intel card and a Linksys USB wireless N (Gigabit) card (MARVELL) on an Intel dual-core 3G (actually 2.8G) CPU with 1G RAM on the box.

What I would like to do is to dedicate one network interface to Firefox, and the other to everything else that needs a network interface.

I've searched, via Google, but haven't found anything viable.  (Of course, I'm not certain what search terms to use for this:confused:.)

I'm running Ubuntu/Hardy (8.04) with a Gnome interface, which, btw, frequently *looses* the network configuration on reboot - about 60%-70% of the time.

I'm on a cable access, but the wireless card only runs at a G level, not N - maybe 256 Kb transfer - so I have the bandwidth available to run both interfaces.

I've tried setting both to the same IP and setting each interface to a different IP, but there's no perceptible difference in performance.

I do a lot of file transfers, some of 'em pretty big, and I'd like to set the 10/100 card to the browser and use the wireless card to effect file transfer and other miscellaneous net activities.

Any possibility?  Any ideas?  I'm open to trying just about anything.

---

### Post by mellowd on 2008-08-17
Why would you try to do this? The bottleneck isn't your interfaces, but rather your connection to the internet itself. This won't speed up anything as both your wired and wireless connection terminate at the same router, and that router terminates at the same IP

---

### Post by databarn on 2008-08-17
> **mellowd said:**
> Why would you try to do this? The bottleneck isn't your interfaces, but rather your connection to the internet itself. This won't speed up anything as both your wired and wireless connection terminate at the same router, and that router terminates at the same IP

mellowd,

As specified, I have greater bandwidth available than either of the cards can avail to me, in fact, more that both cards combined can avail me.

I'm trying to find a way to utilize the bandwidth available to me.

I'm also trying to dedicate a certain amount of that bandwidth to one particular purpose, while allocating the rest to general usage.

The router is not a bottleneck, rather the driver I am able to use for the wireless card is the bottleneck.  Since there are two cards available, I'd like to be able to utilize their combined capabilities.

Lets say I have 512 Mb bandwidth.  The combined cards cannot utilize that full bandwidth.  It's not a bandwidth issue, per se, but one of the combined card's capabilities to address that bandwidth.  If I can use both cards, independently of each other, I can improve throughput by a good 25%, giving me about 75% utilization of the bandwidth available to me.

Again, the available drivers are the throttle point, not the router, nor the cable connection.

I just want to make use of all the resources I have.

Does that make more sense?

I'm aware of the limitations anent the router/cable connection, but they don't really come into play at this point insofar as I'm aware.  This is something I was able to do with WinXP, after a fashion.  I'm just trying to find a way to do it with Ubuntu/Linux.

If I can't *dedicate* one card to a specific purpose w/o another Internet connection, I'd like to at least be able to use the *combined* capacity of both cards to make maximum use of their combined bandwidth.

---

### Post by mellowd on 2008-08-17
What's your available bandwidth? As you have a 100mb card is your bandwidth greater than this?

---

### Post by databarn on 2008-08-17
> **mellowd said:**
> What's your available bandwidth? As you have a 100mb card is your bandwidth greater than this?

As mentioned before, I've at least 512 ... sometimes more, sometimes less, depending upon activity, but I've never seen it fall below 384 +/-.  There are times when the *available* bandwidth borders upon 1G, but that's not something I rely upon.

Best driver I've found for the MARVELL chip set is pretty much limited to 256 Mb, and the Intel card is, of course, limited to 10/100 Mb.

So, on my *worst* days, I'd not be able to exceed available bandwidth, ya know?

---

### Post by mellowd on 2008-08-17
You saying you have half a gig of internet bandwidth avaiable to your PC, How is this possible?

I know you can lock an application to use one particular interface, say for example you are running a database and want one card just transferring data for that, you can do it. But it all depends on the application itself. It looks like firefox doesn't allow this.

---

### Post by databarn on 2008-08-17
> **databarn said:**
> 
So, on my *worst* days, I'd not be able to exceed available bandwidth, ya know?

However, my query, at this point, is whether it's possible to dedicate a certain amount of bandwidth to the browser within Ubuntu - or any other Linux flavour, for that matter - with or without multiple network interfaces.  

As mentioned, I've kinda, sorta accomplished this with WinXP, but it was a horrible kludge, and not entirely reliable.  I'd tell ya how, but that disappeared with my last XP crash - I ***hate*** backups that don't restore, but that's another thread <sigh />.

---

### Post by mellowd on 2008-08-17
What kind of file transfers do you do?

You might be able to do what you accomplish via QoS on your router, if it supports that.

You can give a far higher priority to web traffic as opposed to say ftp traffic.

It's how we prioritise voice packets through networks here at work

---

### Post by databarn on 2008-08-17
> **mellowd said:**
> You saying you have half a gig of internet bandwidth avaiable to your PC, How is this possible?

I know you can lock an application to use one particular interface, say for example you are running a database and want one card just transferring data for that, you can do it. But it all depends on the application itself. It looks like firefox doesn't allow this.

First of all, don't confuse Mb with MB ... rule of thumb, divide Mb by ten to get functional MB ... eight bits = 1 Byte, and add two bits for overhead ... so that half-a-gig of bandwidth boils down to about 51 MB, i.e., 512 Mb ~= 50+ MB.

Bandwidth is always, unfortunately, measured at the highest possible number, just as is disk space.  So, my bandwidth is not measured in *characters* (8-bit ... UTF8 is larger) but in the *particles that make up the characters*.  As I said, divide by ten and you'll get a more realistic picture of real data transfer.

I guess what I'm asking for is, perhaps, a channel, one that will let me allocate a given amount of traffic space to a give application.  This would necessarily be, I think, an OS allocation, not an application-specific allocation.

But I cannot seem to find anything in Linux that will allow said allocation.

Hey, it's late, and I'm prolly not makin' a lot of sense right now ... I'll try again tomorrow <yawn />.

---

### Post by mellowd on 2008-08-17
> **databarn said:**
> First of all, don't confuse Mb with MB ... rule of thumb, divide Mb by ten to get functional MB ... eight bits = 1 Byte, and add two bits for overhead ... so that half-a-gig of bandwidth boils down to about 51 MB, i.e., 512 Mb ~= 50+ MB.

Bandwidth is always, unfortunately, measured at the highest possible number, just as is disk space.  So, my bandwidth is not measured in *characters* (8-bit ... UTF8 is larger) but in the *particles that make up the characters*.  As I said, divide by ten and you'll get a more realistic picture of real data transfer.

I guess what I'm asking for is, perhaps, a channel, one that will let me allocate a given amount of traffic space to a give application.  This would necessarily be, I think, an OS allocation, not an application-specific allocation.

But I cannot seem to find anything in Linux that will allow said allocation.

Hey, it's late, and I'm prolly not makin' a lot of sense right now ... I'll try again tomorrow <yawn />.

I'm well aware of that, I'm a network admin :) I didn't say gigabye of bandwidth, just half a gig ;)

---

### Post by roquefilipe on 2008-10-26
I would also like to know if such a thing as these is possible. 

I am currently experimenting with the firmware of a router, trough eth0, and I would like to be connected to the internet, trough wlan0, simultaneously. 
Having to manually switch connections each time I try something with the first router is pretty boring. 

By the way I now that the ping command can ping on specific network interfaces, trough -I switch.

---

