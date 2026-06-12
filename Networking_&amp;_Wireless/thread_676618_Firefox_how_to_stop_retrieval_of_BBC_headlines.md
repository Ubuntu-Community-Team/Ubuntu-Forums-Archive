---
title: "Firefox: how to stop retrieval of BBC headlines?"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by strangerep on 2008-01-23
I have a slow dialup internet link. Sometimes when I start firefox,
it seems to saturate the link for a while downloading BBC news
(at least, that's what I interpret from my tcpdump output).
Until it finishes, any other attempted domain name lookups just
time out (sigh).

Is there a config item in firefox that disables this? I've looked
in about:config, but didn't find anything obviously relevant.

(This is running on Feisty, in case that makes a difference.)

TIA.

---

### Post by Shazaam on 2008-01-24
This is all I could find in about:config.... nothing on mozillazine.

browser.feeds.handler

Mine is set to ask.

---

### Post by strangerep on 2008-01-24
> **Shazaam said:**
> This is all I could find in about:config.... nothing on mozillazine.

browser.feeds.handler

Mine is set to ask.

Mine too.

But I just realized that the BBC headlines icon is a "live" bookmark.
So I went into "Organize Bookmarks" and deleted it completely.
That made the icon disappear.

Hopefully the "live" bookmark is now well and truly dead.

---

