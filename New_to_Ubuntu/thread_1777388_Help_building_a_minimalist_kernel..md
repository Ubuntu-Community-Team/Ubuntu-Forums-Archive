---
title: "Help building a minimalist kernel."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by P=NP on 2011-06-07
I've managed to successfully build a kernel, but I would like to build a minimalist one with only the drivers/modules that are needed for my hardware. I've set a cronjob to run

```
#!/bin/bash

DBFILE=$HOME/mp.log

[[ -f $DBFILE ]] || touch "$DBFILE" || exit 1

lcbefore=$(wc -l < "$DBFILE")
comm -23 <(awk '{print $1}' /proc/modules | sort) <(sort "$DBFILE") >> "$DBFILE"
lcafter=$(wc -l < "$DBFILE")

new=$(( lcafter - lcbefore ))
(( new )) && echo "Found $new new modules"

exit 0
```every five minutes for a couple of weeks. I would like to build a kernel with only these modules.

Can someone point me in the right direction?

---

### Post by Capoeira on 2011-08-24
localmodconfig

---

### Post by jtarin on 2011-08-24
Though I haven't used it for some time [this one]("http://www.tuxradar.com/content/how-compile-linux-kernel") has always been my favorite method.Just keep a good back-up kernel until you feel you have gotten it right.
> It also follows that when you update your kernel, and this includes recompiling the same version, you then need to reinstall any packages that installed their own modules.

There is also [this]("http://kcheck.sourceforge.net/about.html") , but I haven't used it so can't vouch for it.

---

