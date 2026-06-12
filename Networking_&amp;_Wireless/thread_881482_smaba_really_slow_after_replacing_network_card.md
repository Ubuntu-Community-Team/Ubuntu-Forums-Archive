---
title: "smaba: really slow after replacing network card"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by bsh on 2008-08-06
hello

i had issues with the network card i was using, so i replaced it.

since then, writing to samba (from windows clients) is painfully slow.

reading from samba is still fast (even faster than with the old network card!)
using ftp, i get really good speeds in both directions.
so i think the problem is not the network card, as it works with ftp. (tested with iperf too)

some speed values:
ftp download from the machine: 40mb/s
ftp upload to the machine: 35mb/s
samba read ("download"): 25mb/s
samba write ("upload"): 0,2-4mb/s, fluctuating, 1-2mb/s on average.

but i don't understand how a network card change would slow samba writes down???
any useful ideas?

btw, i am on a gigabit network.

---

