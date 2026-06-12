---
title: "ltsp client slow"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by subhan on 2007-04-16
hai

my name is subhan.
i installed ltsp on my system.
 i connected 5 clients to the server.
now clients become very slow.
Server machine as 2 GB Ram and 80 GB HARDDISK.
PLEASE GIVE A SOLUTION 

THANKS
SUBHAN

---

### Post by joebaker on 2007-04-18
It is common for distributions to include desktop search tools which index home directories and other public files on the system.  When all your users start doing this at the same moment, it can tax the system dramatically.  Beagle was one such application under Gnome that did this.

Something to consider anyway.  Make sure you're running a network switch.  Go over your name service again.

Good Luck!

---

