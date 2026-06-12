---
title: "Slow GMail + &quot;lost or reordered&quot; packets"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by cygnus81 on 2007-06-14
I'm frustrated. For quite some time I have a weird problem. Accessing Gmail from my computer is terribly slow (takes a couple of minutes for each action - logging in, viewing a message, deleting, etc).
Some properties of the problem:
[LIST]
[*]It only happens with Gmail website. No other website.
[*]It happens 98% of the time. I can have at top, one hour a day (mostly really late at night) when Gmail works fast like it should.
[*]I get no error messages.
[*]**It happens only from my computer.**
[*]POP3 access is also slow like hell.
[*]If I look at my modem (cable) the lights indicate no action (it's just like my computer is waiting for something. more on that later).
[/LIST]
Some things I've tried to do:
[LIST]
[*]Clear the browser cache, cookies (and all the private data) and restarting the browser (Firefox).
[*]Use the "basic HTML" view in Gmail.
[*]Post a message in Gmail support groups - no replies...
[*]Disable my firewall (guarddog).
[*]Disable my ip blocker (peerguardian).
[/LIST]
All to no avail.

What's it got to do with my Ubuntu ?
Well, my syslog contains lots of 
```
pptp[6820]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 105743 (expecting 105742, lost or reordered)
``` messages.
I really don't know if thats related (since I **do** have fast access from time to time).
All in all - the problem seems too sporadic - I couldn't figure out where it originates.

Can these "lost or reordered" packets be related ? What is that exactly ?

---

### Post by ariel on 2007-06-28
I also notice a gmail-only slowness, mainly for the initial login. Did you fix your problem?
In my case it seems to have started happening since I replaced my wireless pci card.

 I'm using a wg311t which works perfectly, awesome throughput and all. The only quirk is that gmail login takes half a minute or so. weird.

---

### Post by cygnus81 on 2007-06-30
> **ariel said:**
> I also notice a gmail-only slowness, mainly for the initial login. Did you fix your problem?
In my case it seems to have started happening since I replaced my wireless pci card.

 I'm using a wg311t which works perfectly, awesome throughput and all. The only quirk is that gmail login takes half a minute or so. weird.

I opened port 80 on my firewall (incoming) and it seems just slightly better. I have no idea how I was able to surf the web before (when it was close). But all in all, its more likely that it has nothing to do with the firewall - since it still happens quite a lot.

By the way, I'm not on a wireless connection..

---

### Post by Soarer on 2007-06-30
> **cygnus81 said:**
> I opened port 80 on my firewall (incoming) and it seems just slightly better. I have no idea how I was able to surf the web before (when it was close). But all in all, its more likely that it has nothing to do with the firewall - since it still happens quite a lot.

By the way, I'm not on a wireless connection..

You don't need an incoming port open to surf - your firewall detects incoming *replies* to browser queries and lets them through. Opening port 80 will let unsolicited queries in, which may be mischievous. Unless you are running a webserver, it should normally be closed incoming.

I get a hang-up sometimes on Ubuntu documentation, whilst it goes looking for a ssl.google-analytics link - maybe just waiting for a busy authentication server?

---

