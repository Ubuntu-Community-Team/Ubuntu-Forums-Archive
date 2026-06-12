---
title: "Internet works then doesn't work :S"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by chris19 on 2008-11-15
Hi,

I've had a new laptop for about a month now, set it up for duel boot XP/Ubuntu, but I don't use Ubuntu much because my internet doesn't work all the time (most of the time)... on XP is works all the time.

I'm going through a wired connection - DHCP. Free roaming is enabled, and so is connection.

I haven't really done much by setting it up :S... it just tends to work on the off chance.

What configurations should I have done initially? Is it just a case of 'plug and play' - because this is what I've effectively done.

Could it be anything to do with drivers?

Thanks for any help... I'm really keen to use Ubuntu, but with no internet I can't :(

---

### Post by chris19 on 2008-11-15
I've done some tests... something called 'Ping'?

Well I had 0% successful packets... which means I have poor connection or it doesn't recognise my internet :(

Any help please?

---

### Post by chris19 on 2008-11-15
Anyone? :(

---

### Post by alecz20 on 2008-11-15
Next time the internet doesn work, try running this in terminal:

```

gksu /etc/init.d/networking restart

```

---

