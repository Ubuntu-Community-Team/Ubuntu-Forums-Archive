---
title: "Will Ubu Run On This Mini Netbook?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by mapes12 on 2010-02-28
Hi

Does anyone know if a version of Ubu will run on one of [these? ]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=230427685200&fromMakeTrack=true&ssPageName=VIP:watchlink:top:en")

Thank you.

Mark

---

### Post by TheBuda on 2010-02-28
Yes it will, but you'll need to be very creative in your installation.  once you get the kernel installed, a desktop environment, wifi working, a browser installed you'll fill about 75% of the HD.  You can probably get it around 1Gb but you'll thin its ugly.

I've been working with my Mini 9 with a 4Gb HD and I'm at 1.9 gig.

---

### Post by Arkitekt on 2010-02-28
take a look at Ubuntu Netbook Remix if you haven't already, it is specifically designed for netbooks and their lower specs and smaller hard drives.

---

### Post by mapes12 on 2010-02-28
Thanks guys,

All I want it for is to take to meetings to make my notes and then transfer them to my main Ubu system. So, storage isn't an issue because I only want to create text files............and that's it! My hand writing is rubbish.

Without a CD/DVD drive any ideas how to install?

---

### Post by Arkitekt on 2010-02-28
Well, a barebones UNR with almost everything removed would do the trick lol, make sure Tomboy is on there and then you can sync your notes with a Ubuntu One account if you haveone, makes for easy transfering to your other Ubuntu system

---

### Post by TheBuda on 2010-02-28
I did an install from the minimal CD (put it on a USB stick, worked like a champ) and have had great results. I'd avoid the netbook remix and just go straight gnome and open office.  Just install the barebone kernal then:

```
sudo aptitude install gnome-core gnome-power-manager gnome-utils openoffice.org-writer xpdf
```

shoudl take care of everything at around 1Gb

---

### Post by davec64 on 2010-02-28
I see it's got an ARM processor, so you'll need to investigate one of these versions:

[http://www.ubuntu.com/products/whatisubuntu/arm]("http://www.ubuntu.com/products/whatisubuntu/arm")

Depending on the platform. :)

Off the top of my head, I don't think UNR supports ARM processors.

---

