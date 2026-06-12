---
title: "Lightest, best alternative to Deluge torrent client?"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by logos34 on 2008-09-04
Well, as much as I like the idea of Deluge, with its plugins, webpage gui, native linux application, gnome desktop integration, etc., it's a real memory hog.  Uses ~9% of RAM.  

Unless anyone can convince me otherwise, I think I'm going back to uTorrent (only uses ~3% of my avail. RAM).  That's a big spread.  I'm not crazy about wine, and try to avoid it whenever an equivalent or better linux app is available, but in this case I see no other way.  

Azureus is to be avoided like the plague (all that java crap), I know that. 

What client do you use and why?  How light?

---

### Post by rampageoberon on 2008-09-04
I personally like rtorrent. Its a very light and command line client. It does everything I need but individual torrent throttling and rss feeds. But its an excellent client, and a plus you can manage torrents remotely via ssh.

With regards to ram usage it uses minimal ram when torrenting at normal speeds (standard home ADSL) but on faster connections it takes more resources as expected.

---

### Post by kaivalagi on 2008-09-04
You could try transmission? It has a smaller foot print than Deluge and still have a standard GUI...

rtorrent is good though if your okay with a curses based console app :):)

---

### Post by logos34 on 2008-09-04
ok, I using transmission now...HALF the % ram footprint of  deluge.  That's more like it.  But  pretty bare bones options-wise.  I 'll download rtorrent next and ease my way into a CLI client.  Some things I prefer a gui for (as long as not too heavy), other things I'm just as at home using the terminal.

---

### Post by tact on 2008-09-04
if lightweight doesn't mean CLI only, permitting/desiring a GUI...  have a look at qBittorrent.   Thats my current tool.

Cheers

---

### Post by logos34 on 2008-09-06
> **rampageoberon said:**
> I personally like rtorrent. Its a very light and command line client. It does everything I need but individual torrent throttling and rss feeds. But its an excellent client, and a plus you can manage torrents remotely via ssh.

With regards to ram usage it uses minimal ram when torrenting at normal speeds (standard home ADSL) but on faster connections it takes more resources as expected.

I'm on adsl too.  I've got rtorrent going now (not the most intuitive CLI app out there, gotta say, takes a while to get your bearings)...It weighs in at less than half the ram usage of transmission--averages ~12-15 MB.  I think this is the ticket.  Then again there's also transmission-cli/-remote.  But there's a lot of rtorrent fans, and there must be a reason, so maybe that's the better choice  

I think I've got the right settings in .rtorrent.rc.  Again, the official documentation could be clearer and I couldn't find a single really good setup/config howto.  Recommend one?

No matter how much I try to cut down memory usage, it seems to be a losing battle--there always seems to be something waiting in the wings to take up ram.

---

### Post by logos34 on 2008-09-06
What are these messages I keep getting on the main page below each torrent:

> Storage error: [File chunk write error: Success.]

and 

> Tracker: [Tried all trackers.]

??

I'm behind a router, so I have the recommended settings for udp 'off':
> 
use_udp_trackers = no

Otherwise everyhting seems to work ok

---

