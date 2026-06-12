---
title: "[SOLVED] How can I make Tor use only US proxies?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-12-05
I'm curious to find out how I can make Tor use only US proxies.

It is currently giving me proxies from all around the world.

I haven't tried Vidalia because it won't run and just crashes.

Any ideas are appreciated! Thanks in advance!!

---

### Post by pluckypigeon on 2008-12-06
If anyone actually cares you have to edit /etc/tor/torrc

.................

go to [https://torstat.xenobite.eu/](https://torstat.xenobite.eu/) 

in the CC: box select US and then click search

then click the ">" below Exit, this will give you a list of exit node nicknames.

open torrc 

```
gksudo gedit /etc/tor/torrc
```

paste this right at the bottom

```

StrictExitNodes 1
exitnodes PUT, NICK, NAMES, HERE, SEPARATED, BY, COMMAS

```

replace:
PUT, NICK, NAMES, HERE, SEPARATED, BY, COMMAS with the nicknames you got from the search. You only need about 10.

Don't use this for anything illegal

---

### Post by SamNSane on 2008-12-06
Thank you for posting this information, **pluckypigeon**. I'm interested, and I'm glad you did the research and posted the solution you found.

---

### Post by pluckypigeon on 2008-12-06
> **SamNSane said:**
> Thank you for posting this information, **pluckypigeon**. I'm interested, and I'm glad you did the research and posted the solution you found.

No problem. Glad I could help.

---

### Post by pluckypigeon on 2008-12-08
...

---

### Post by Dr Small on 2008-12-08
+1 for solving the problem and documenting it ;)

---

### Post by pluckypigeon on 2008-12-08
Also if you are in the US and if it's legal you could use it to watch BBC Iplayer.

Just search UK instead of US. Only do it if it's legal though!

---

