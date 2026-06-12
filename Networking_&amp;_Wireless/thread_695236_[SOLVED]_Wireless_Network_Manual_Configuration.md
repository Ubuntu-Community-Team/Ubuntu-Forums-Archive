---
title: "[SOLVED] Wireless Network Manual Configuration"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2008-02-12
at one point I had manual configuration working where everytime I started up I didn't have to do any thing to connect. I was testing things and enabled roaming mode and now i am unable to connect using manual configuration. Any idea's?

---

### Post by pytheas22 on 2008-02-12
how did you have manual connection set up?  Did you write a script or do you mean that Network Manager automatically connected you?  Roaming mode is enabled by default for me; had you unenabled it for some reason?

---

### Post by tad1073 on 2008-02-12
> **pytheas22 said:**
> how did you have manual connection set up?  Did you write a script or do you mean that Network Manager automatically connected you? 
I mean Network Manager 

> **pytheas22 said:**
> Roaming mode is enabled by default for me; had you unenabled it for some reason?
Yeah, i was just testing things, I like to tinker with stuff, usually until I break it.:lolflag:

---

### Post by pytheas22 on 2008-02-12
ok, thanks for the information.  Are you able to connect wirelessly now, and if so what do you have to do?  Did you try reversing the things you did when you were tinkering (sorry if that's a stupid question, but I just want to be sure)?

---

### Post by tad1073 on 2008-02-12
> **pytheas22 said:**
> ok, thanks for the information.  Are you able to connect wirelessly now, and if so what do you have to do?  Did you try reversing the things you did when you were tinkering (sorry if that's a stupid question, but I just want to be sure)?

Yeah, I just enabled roaming mode again. When you reenable it though, you have to select connect to other wireless network and enter in you information again.

---

### Post by pytheas22 on 2008-02-13
I don't have any very good ideas, but here are a few possible solutions:

1. purging and reinstalling NM might help:

```
dpkg --purge network-manager
```

then reinstall it via Synaptic, along with all the dependencies that will get purged along with it.  Everything should be on the Gutsy installation CD, so you don't have to worry about losing your wireless if you don't have a wired connection to back it up.

2. you could write a script to autoconnect and run it at boot or whenever.  This page [http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html) should help you figure out what commands you would need to include.

3. try using wicd instead of NM.  I believe that you can set it to autoconnect.  You will probably have to uninstall NM before installing wicd.  wicd site is [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) 

Again, I don't think that any of these suggestions is that great, and if I were you I would wait longer to see if someone else has better ideas.  These are all just workarounds that might help you out if all else fails, but they don't address the root problem, and I don't know enough about what NM does in the background to go about doing that.

---

### Post by tad1073 on 2008-02-13
I am afraid to do that for fear of not being able to get my wireless conecction back. Albeit, I could plug into the router but I am done with lugging that thing up and down the stairs.

---

### Post by pytheas22 on 2008-02-16
Network Manager and its dependencies are on the Ubuntu installation CD, so if you uninstall them they can be reinstalled without an Internet connection.

Also, if you wrote a script to autoconnect, you wouldn't have to remove NM.

Unfortunately, I still don't have any better ideas, and I'm sorry that no one who does has responded...

---

### Post by tad1073 on 2008-02-16
No worries. I installed Wicd and everything works like a charm.  The only problem I am having is when I do:

```
sudo iwconfig ath0 rate 54M
```
sometimes it will connect at that rate and sometimes it won't

---

### Post by pytheas22 on 2008-02-16
That could be because of a spotty signal.  If you're sort of far away from the router you won't be able to connect at full speed I think.  You could try moving your antenna/computer around a little bit and see if it makes a difference.  In my experience, a centimeter literally could be the difference between no connectivity and a great connection, when I was using the neighbors' networks and was far from their APs.

Anyway as long as you still get decent download speeds and latency, the rate shouldn't matter too much, should it?  Unless you're lucky enough to have a 54mbs Internet connection...

EDIT: also, as you have an Atheros card, I think that madwifi might use a different command to adjust rate; maybe iwpriv?  Or maybe you have to create a virtual interface at the rate you want.  madwifi does things in special ways sometimes.

---

### Post by tad1073 on 2008-02-16
> **pytheas22 said:**
> That could be because of a spotty signal.  If you're sort of far away from the router you won't be able to connect at full speed I think.  You could try moving your antenna/computer around a little bit and see if it makes a difference.  In my experience, a centimeter literally could be the difference between no connectivity and a great connection, when I was using the neighbors' networks and was far from their APs.

Anyway as long as you still get decent download speeds and latency, the rate shouldn't matter too much, should it?  Unless you're lucky enough to have a 54mbs Internet connection...

EDIT: also, as you have an Atheros card, I think that madwifi might use a different command to adjust rate; maybe iwpriv?  Or maybe you have to create a virtual interface at the rate you want.  madwifi does things in special ways sometimes.

i am on the second floor and the router is on the first my signal strength fluxuate's betweem 20% and 30%.

My download speed is around 150kbs or so.

i have been reading the madwifi manual and the command is iwconfig, iwpriv is for other stuff but i can't remember of the top of my head, being that the manual is about 45 pages long.

---

### Post by pytheas22 on 2008-02-16
20-30% signal strength isn't that good, although from what I understand signal strength is sort of arbitrary; the only thing that really matters is whether you're connected or not.

Nonetheless, I can tell you that my Atheros card, even with a fancy external antenna, reports very poor signal strengths using madwifi, although in Windows it's much better.  Even so, the connection still works fine, although I don't pay attention to rate (my ISP cripples my connection to limit download speeds to about 80kb/s and I don't have any kind of local network set up, so I don't care that much).  I have read of others having similar problems with madwifi signal strength.  If it matters a lot you could try using ndiswrapper.  But make sure first that it supports 54mbs, as I believe that it was limited to 11mbs, a couple years ago.

---

### Post by tad1073 on 2008-02-16
I am just going to stick with madwifi for now. From my underatanding when Hardy is released ATH5K will be released with it. I know the 2.6.24-rc5 xen kernel come with ATH5K. 

Speaking of home networks... I am able to access xp from ubuntu but I can't access ubuntu from xp. I can ping my ip address but that is it... any thoughts?

Here, check [this thread out](http://ubuntuforums.org/showthread.php?t=678868) . It explains what is goning on with that issue.

---

### Post by pytheas22 on 2008-02-16
I don't really have any experience with samba and all that, unfortunately...although I do know that sometimes when I try to access network shares (between Ubuntu machines using the samba protocol) in Nautilus, it sometimes doesn't work unless I put the IP address of the machine I am trying to access in the address bar.  Otherwise it complains and doesn't show the share.  I think this is a relatively common problem but it's never been enough of an issue for me to fix.

Unfortunately that's about all that I can say about samba; good luck.

---

