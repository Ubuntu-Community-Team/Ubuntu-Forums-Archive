---
title: "Wifi network drops"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Nano on 2008-02-19
Hi everyone.
I'm experiencing a very weird problem.

I have a PCI wifi card which is correctly working on my 7.10, however, from time to time the connection drops and I have to "/etc/init.d/network restart" in order to make it work again.

The card is recognized as:
```

02:07.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

```

It worked out of the box as soon as I installed Ubuntu.

What can I do to see what the problem is?

From dmesg I see this but it doesn't make a lot of sense to me:
```

[530812.312000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[530812.328000] wlan0: Initial auth_alg=0
[530812.328000] wlan0: authenticate with AP 00:16:e3:1e:e2:57
[530812.332000] wlan0: RX authentication from 00:16:e3:1e:e2:57 (alg=0 transaction=2 status=0)
[530812.332000] wlan0: authenticated
[530812.332000] wlan0: associate with AP 00:16:e3:1e:e2:57
[530812.332000] wlan0: RX AssocResp from 00:16:e3:1e:e2:57 (capab=0x411 status=0 aid=8)
[530812.332000] wlan0: associated
[530812.336000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[530813.156000] wlan0: duplicate address detected!

```

---

### Post by jhetrick62 on 2008-02-19
How close is this to the router?  You may be throwing errors in your transmission that occasionally depending on the data load cause you an issue.  If this is the case, install the windows drivers using ndiswrapper.

I built a machine for my brother in-law and built it in the same room as the router so when we istalled wireless it seemed to work fine.  Took it downstairs and had all lkinds of problelms after no changes.  It was tossing errors in the communications stream which did not bother it much when close, but heavily when 50 ft away.  Installed the windows drivers with ndiswrapper and it works like a champ.

BTW, ours was a ralink chip also.

Jeff

---

### Post by Nano on 2008-02-19
Thanks for your reply.
This PCI network card has a wired antenna which is at 3m from the router without obstacles in the middle, so it's not a matter of reception. :(

Actually, in another Ubuntu box I have the same antenna and it works perfectly.

Sometimes it drops every 30 seconds, sometimes it lasts hours without dropping.

What could it be, people?

Thanks again for your attention.

---

### Post by Dragabain on 2008-02-19
I'm having the same problems with my card.  I'm trying to download a large file (or move) from my laptop to my desktop and the driver keeps crapping out on me.  Is there any other way to remedy this without resorting to ndiswrapper?

---

### Post by jhetrick62 on 2008-02-19
Install the windows driver in ndiswrapper and blacklist the current driver.  Sadly it the best option for many of the wireless cards in Linux.

Jeff

---

### Post by Dragabain on 2008-02-21
Just as an fyi, I upgraded to kernel 2.6.24 and it seems all those issues are ironed out now.  I forget where I found the forum post but a guy has a nice python installer for the hardy harron kernel.

---

