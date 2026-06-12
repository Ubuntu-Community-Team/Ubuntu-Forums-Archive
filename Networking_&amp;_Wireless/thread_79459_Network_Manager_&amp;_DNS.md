---
title: "Network Manager &amp; DNS"
date: 2005-10-20
forum: Networking &amp; Wireless
---

### Post by Soko on 2005-10-20
Is there an approved way of telling Network Manager to not use a local caching name server on ubuntu? I use split DNS on my network and the current config is not working when I go from the office to home.

An alternative solution would be to get named to flush it's cache once it detects that the machine has moved from one IP subnet to another.

Thanks for any help on this,

Soko

---

### Post by mlambie on 2005-10-21
This might be what you're after. I'm testing it out now.

[http://wildbill.nulldevice.net/archives/000144.html](http://wildbill.nulldevice.net/archives/000144.html)

edit: I didn't have any luck, and resorted to installing the network-manager package available in the repos. Local bind isn't a *huge* issue for me...

---

