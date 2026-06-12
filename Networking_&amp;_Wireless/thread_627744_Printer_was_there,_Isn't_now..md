---
title: "Printer was there, Isn't now."
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by metro.tramp on 2007-11-30
I'm not sure if this should go in the Noob thread, but:

I recently got a Samsung HP-2010 laser printer for uni work etc.

I plugged it into my server/general use Ubuntu (7.10) box and it auto-installed absolutely fine. Printing worked fine and I was pleased to discover that the printer was automatically shared on my network - I could print straight away from my mac laptop with no problems at all.

Then my ubuntu box went a bit wrong for a while - it wouldn't play sound, so I ran a reinstall of ausio packages, which somehow got rid of some gnome stuff... yada yada...

I got gnome backu and running, sound working fine, but my printer was no longer shared on the network...

I would try to load the details manually through my mac, but i can't work out what address to point it to. The boxes are ticket to share the thing in the printers section of the admin bar, but I can't find what address it's shared at.

I would look into CUPS settings, but I don't even know if this stuff is running with CUPS or what?

So I'm stuck - the printer prints fine through the box, but as I spend most of my time on my laptop, I really want to be able to print through the network again, but I have no idea what config files to play with/delete to make it all work nicely again....

---

### Post by froy02 on 2007-12-01
Open your fireox browser and type 'http://localhost:631' and see if you can configure your printer from there.

---

