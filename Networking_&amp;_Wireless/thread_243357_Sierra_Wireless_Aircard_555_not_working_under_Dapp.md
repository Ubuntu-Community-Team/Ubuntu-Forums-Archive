---
title: "Sierra Wireless Aircard 555 not working under Dapper"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by mstokes on 2006-08-24
This card worked fine under Breezy, but with the new pcmcia-cs support, I have not found instructions that work correctly.

The card is not recognized when inserted in the pcmcia slot.  I would appreciate any ideas.

Thanks
Mike

---

### Post by tjkopena on 2006-11-03
For the record in case anyone else is looking for help with this, the real problem is related to either the specific kernel or pcmciautils problem that shipped with Dapper.  It's fixed under Edgy Eft.  I've put up specific notes on where to put CIS data files and such under Ubuntu here: [http://gicl.cs.drexel.edu/people/tjkopena/wiki/pmwiki.php?n=SWAT.Aircard555]("http://gicl.cs.drexel.edu/people/tjkopena/wiki/pmwiki.php?n=SWAT.Aircard555").

---

