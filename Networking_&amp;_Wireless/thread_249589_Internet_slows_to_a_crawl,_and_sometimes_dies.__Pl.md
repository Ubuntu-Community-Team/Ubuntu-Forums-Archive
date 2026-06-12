---
title: "Internet slows to a crawl, and sometimes dies.  Please help!"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by alyson on 2006-09-02
I'm experiencing some major weirdness with internet connectivity.  My internet connection is slowing down to an unusable state, then speeding back up to normal, then slowing down again, etc.  Mostly, however, it remains so slow I can't even use it.  Synaptic, Firefox, Epiphany--they're all doing the same thing.

So, here's some background info and a bit of a summary:
[LIST]
[*]I disabled IPv6 in Firefox (since this seems to be the most popular solution; curiously, many people have commented that it doesn't actually help), to no avail.  I also tried disabling IPv6 system-wide, but this didn't help, either
[*]I'm getting a 100% wireless signal at all times
[*]The connection slows down even when I plug into the router
[*]The connection occasionally speeds back up to a perfectly usable state, then, after about 30 seconds to several minutes, slows back down to an unusable state for several minutes.  This cycle continues throughout use
[*]I set aside an IP for this laptop from the router, and it's using the assigned IP
[*]I deactivated the non-wired connection (somebody recommended this in another thread), and this didn't help
[*]Wireless internet is working perfectly on another Ubuntu 6.06 laptop here
[*]The wireless card is an Intel/PRO Wireless 3945 internal card; the laptop is a Dell Inspiron E1405
[*]I've rebooted after toggling settings about a million times: still, no dice
[*]When I compare the ifconfig of the laptop with functional connectivity with the busted one, everything looks the same (except for the IPs, of course), but the busted one has 35 dropped RX packets out of 4044.  Does this mean anything?
[*]iwconfig shows a lot of "invalid misc"--is this bad?
[*]When I ping different addresses, I see a (DUP!) every few packets.  Does this mean anything?
[/LIST]

So has anyone out there experienced this problem and solved it?  Did I overlook a solution in the forums?  I've never experienced something so crummy with Ubuntu that I haven't been able to fix, so I'm hoping that this problem will be no different.  This laptop will mostly be used for internet stuff, and I know Windows will do the trick, but I'd rather not go that route.  All of the standard fixes--disabling IPv6, in particular--don't seem to work here.  Help?  Please?

---

### Post by drtvasudevan on 2006-09-02
there are a few problems and so no single solution works
ipv6 is a basic problem and so unless you are in japan keep it disabled.

hope you are able to ping named sites.

you might have tried this...
in terminal gksu gedit /etc/network/interfaces
if not present add a dns-nameservers xx.xx.xx.xx

the xx being your ISP's DNS

---

### Post by brim4brim on 2006-09-02
> **alyson said:**
> So I convinced a friend to install Ubuntu on her new laptop, since I've had such great experiences with the OS.  Wireless internet worked fine with the LiveCD, so we went ahead and installed Ubuntu 6.06.1 this morning.  

However, now that we've installed it, we're encountering serious problems with internet connectivity.  For the first few minutes, everything seems to work well enough; browsing seems a bit slow, but it works fine.  Then, quite suddenly, it slows to an unusable state.  Pages sometimes take five minutes to load, or they won't load at all.  Synaptic is similarly unusable (which is quite frustrating, as I had picked a bunch of apps for installation, and I was like, "Okay, these should install in a snap, and you'll be good to go!"--then we were informed that it would take something like 29 days because everything was downloading at about 200 bytes per second).  

So, here's some background info and a bit of a summary:
[LIST]
[*]I disabled IPv6 in Firefox (since this seems to be the most popular solution; curiously, many people have commented that it doesn't actually help), to no avail
[*]We're getting a 100% wireless signal at all times
[*]The internet seemed to work fine with the LiveCD
[*]We set aside an IP for her laptop from the router, and it's using the assigned IP
[*]I deactivated the non-wired connection (somebody recommended this in another thread), and this didn't help
[*]Wireless internet is working perfectly on my Ubuntu 6.06 laptop
[*]Her wireless card is an Intel/PRO Wireless 3945 internal card
[*]The internet works for a few minutes after a reboot, although turning the wireless card off, then on, doesn't seem to help
[*]I've rebooted after toggling settings about a million times: still, no dice
[*]I've read dozens of posts about slow internet, and nobody seems to have an answer that actually works.  I'm about ready to pull out my hair.  I've been working on this all day, and I'd really just like to finish setting up her system so we can get on with the day.
[/LIST]

Any help is greatly appreciated--not only by me, but probably by the multitudes of other users who seem to have similar problems.  I'm keeping my fingers crossed, as I'd rather not go through a reinstallation of Windows just so my friend can actually use the internet.

Intel/PRO Wireless 3945 internal card

Try updating from Intel's website's drivers.  When I first used Ubuntu a couple of years ago I had this problem with my card and I had to get the drivers from their website directly as the ones in Ubuntu worked for a while but then Internet connectivity would go altogether after a half an hour or so.  These problems were fixed for my laptops card but maybe there is a problem with Intel's drivers for your friends.

It's worth a shot if nothing else is working :-D 

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

^ where I got my driver for when I had to do it.  Don't know if it supports your card or anything so you'll have to check that out.

Otherwise the search i used to find that in google:
[http://www.google.com/search?client=opera&rls=en&q=intel+linux+wireless&sourceid=opera&ie=utf-8&oe=utf-8]("http://www.google.com/search?client=opera&rls=en&q=intel+linux+wireless&sourceid=opera&ie=utf-8&oe=utf-8")

---

### Post by alyson on 2006-09-03
> **drtvasudevan said:**
> 
you might have tried this...
in terminal gksu gedit /etc/network/interfaces
if not present add a dns-nameservers xx.xx.xx.xx

the xx being your ISP's DNS

Her /etc/network/interfaces looks exactly the same as mine, which if I'm not mistaken, is how it should look (i.e. correct WAP and WEP key for eth1).  Won't this just give me another network connection option?

---

### Post by alyson on 2006-09-03
> **brim4brim said:**
> Intel/PRO Wireless 3945 internal card

Try updating from Intel's website's drivers.

Hm.  If nothing else works I'll give it a try, but even when I plug into the router, it's slow, which makes me think the problem isn't with the wireless drivers.  Thanks for the info, though.

---

### Post by alyson on 2006-09-07
I updated the router's firmware, and now everything seems to be working fine;  no more wild fluctuations in connection speed!  Thanks for the suggestions, everyone.

---

