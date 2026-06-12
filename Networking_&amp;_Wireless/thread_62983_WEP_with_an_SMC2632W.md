---
title: "WEP with an SMC2632W"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by brelic on 2005-09-06
Hey,

Does anyone have this card successfully working with WEP enabled?  I have 128bit enabled and working fine in WIndows XP on the same laptop, so it's not a hardware issue.  In Linux, after entering the WEP hexadecimal key, it just doesn't work.  I have tried many things, including flashing the station firmware to a more recent version, to no avail.

USing the Networking GUI, it doesn't give me an error when I enter the WEP key... it just says activating the network for about 30 seconds, then finishes, without internet or network access.  When I use the command-line ```
sudo iwconfig eth1 key [key]
``` it gives me the following error:

```
Error for wireless request "Set Encode" (8B2A)
SET failed on device eth1; Operation not supported.
```

Any ideas?

PS - The card works fine in Linux when WEP is disabled, and I'm using Ubuntu 5.04 (Hoary).

---

### Post by fluteflute on 2008-02-05
I was having this difficulty. The solution was to upgrade the firmware - there were bugs in the firmware which prevented it from working properly under WIndows.

More details: [http://linux-and-oss.blogspot.com/2008/02/smc2632w-wireless-pcmcia-card.html](http://linux-and-oss.blogspot.com/2008/02/smc2632w-wireless-pcmcia-card.html)

I know this thread is over two years old (and the user hasn't logged in for a year) but I thought I'd post in case anyone else comes here (via Google) for the answer.

---

