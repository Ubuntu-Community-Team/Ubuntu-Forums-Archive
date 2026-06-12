---
title: "All Networking Stopped Working (Edgy)"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by rjcarr on 2006-12-04
I installed edgy on a thinkpad a few weeks ago and have been very happy (until today).  The laptop was at work and the wired network worked perfectly out of the box.

I brought the laptop home over the weekend and tried to set up wireless.  It didn't want to look for SSIDs, but when I typed mine in manually, it worked (open wireless, mac filtered).  It seemed there were strange DNS issues, and it would take a while to lookup a site, but once it did the data transfer was about normal.

Then the next morning I turn on the computer and wireless doesn't work.  I try bouncing the interface, my dsl modem, the computer all a few times and nothing.  I turn on my powerbook and wireless is up and working fine.

It seems to be allocated an IP and everything looks normal.  I can even use ping and get responses ... it seems to be limited to TCP maybe?  I get timeouts from both firefox and curl.

I was willing to live with this since this is actually a work laptop and wireless isn't very critical, but I plug it into my dsl modem and it doesn't work there either ... same exact symptoms.  I plug in my powermac and it works fine.  Again I tried bouncing everything and no changes.

The only things I did between when it was working and when it wasn't was install some video apps with synaptic ... gxine, totem-xine, and vlc (in that order, only vlc had the codec I was looking for).  Then I got the flash 9 beta and put the .so in firefox plugins.  That's it.  Since then I've reverted everything and no change.

The only other thing to note is I infrequently get HAL errors when first logging in.  I forget the exact wording, but it pops up in a confirm box when first logging in.  I dismiss it with OK and that's it; I never saw this before I started having the network issues, it seems related.

I don't know of any way to troubleshoot this.  I look at dmesg and it looks fine.  When activing the interface with either ifup or network manager I don't see anything strange.  

Any ideas?  I would really like to resolve this without having to do a reinstall.

---

### Post by Jimmey on 2006-12-04
Make sure the DNS address on this machine is the same as the address being used by the working one.

---

### Post by rjcarr on 2006-12-04
Sorry, but I really don't know what you mean.  The DNS address?  You mean the address of the DNS server?  I don't understand why that is relevant, as DNS is one of the few things that actually works.  

I appreciate the help but please elaborate.

---

