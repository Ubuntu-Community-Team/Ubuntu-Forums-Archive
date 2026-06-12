---
title: "Why does Ubuntu connect to Canonical for no reason? (Hogs link.)"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by strangerep on 2008-01-10
I have only a dialup internet link.
I noticed on my modem lights that sometimes
the link is saturated with receive-data when
I'm not doing anything. Tcpdump reports lots
of traffic to my computer coming from
auckland.canonical.com.www.

Why is this happening? Is it some kind of
automatic update check? If so, how do I
disable it? My dialup link becomes unusable
for other purposes while this is happening.
(Domain name lookups time out because the
dialup link is saturated.)

Also, my computer seems to contact
cf-in-f91.google.com.www periodically
for no reason. Why?

[I'm using Feisty, in case that makes a difference.]

Any advice greatly appreciated...

---

### Post by Hightide on 2008-01-11
HI

yes,its contacting canonical for automatic updates. I will check my books to see if it can be turned off as I have done in XP..

the google one is a bit strange.  

I suppose nothing should be accessing internet without our authorisation.

will get back to you:)

---

### Post by heindsight on 2008-01-11
I don't know about the connections to google, but the connections to Canonical could perhaps
also be for the "popularity contest".

If you go to System > Administration > Software Sources, you can disable automatic checks for
updates on the Updates tab and you can disable submission of statistical information for the
popularity contest on the Statistics tab.

---

### Post by strangerep on 2008-01-11
> **heindsight said:**
> If you go to System > Administration > Software Sources, you can disable
automatic checks for updates on the Updates tab and you can disable
submission of statistical information for the popularity contest on the
Statistics tab.

OK, thanks. I've now changed automatic checking to look only for
the essential Feisty-security updates, and less frequently.
(The statistics-submission feature was already disabled.)

[Hightide: thanks for at least answering my post amongst the endless
deluge of requests for help.]

I'd still like to know what the sporadic google connections are for.
Advertisements perhaps?

---

### Post by Martin Witte on 2008-01-11
are those connections to google happening while you're  browsing pages which have some advertisements delivered by the google service adsense perhaps?

---

### Post by strangerep on 2008-01-11
> **Martin Witte said:**
> are those connections to google happening while you're  browsing pages which have some advertisements delivered by the google service adsense perhaps?

That was my initial thought, but I'm not sure.

It seemed like the google connections were happening in the absence
of me doing anything else (I was trying to load a new page, but I couldn't even
get past the domainname-to-IPaddress stage because my dialup link was
saturated with incoming traffic). But maybe firefox had already loaded part of
the page and was trying to load other stuff. So the correlations are unclear.

Next time I notice it, I'll try to activate tcpdump more quickly and correlate the
results with what I was doing at the time.

---

