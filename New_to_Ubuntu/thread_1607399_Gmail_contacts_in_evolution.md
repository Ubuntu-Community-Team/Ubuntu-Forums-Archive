---
title: "Gmail contacts in evolution"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by driebel on 2010-10-27
Hi, I'm in the process of bringing my various addressbooks (phone, e-mail) into the 21st century and merging them together into one cloud based contact list, maintained on Google and synced to by everything else.  My gmail contact list is organized and ready to go in this regard.  I'd now like to add my gmail contact list to evolution, my preferred mail application, and I've done so using File -> New -> Address book, and setting the type to google.  However, this results in a LOT of doubled contacts (e.g.  my friend John Doe appears as Doe, John and John, Doe).  This does not seem to go away if I wait for the local book to sync with the server, either.  I suspect there is some local cache of my old address book lurking on my system that evolution is using.  Does anyone have any suggestions as to how to find that and make evolution start fresh with the online source?

Thanks,
Dave

---

### Post by driebel on 2010-10-27
Got it.

Evolution cached my online contact list in:

/home/[user]/.evolution/cache/addressbook/[e-mail address]/cache.xml

And was using this file, not the online contact list, to generate the address book.  This file is not deleted when you delete an address book in evolution itself.  Re-creating the address book simply re-loaded this file, with its duplicate entries, rather than updating things.  I deleted that file, re-created the address book from scratch, and all is well.

Dave

---

