---
title: "Kernel update and b43fwcutter"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by yeshmiester on 2008-10-15
I have a broadcom wireless card on my computer and had to load b43fwcutter to get it to work. Every time before this I had to disable/enable the card to get it to work but that wasn't a big issue. 

Today I updated the kernel and now instead of the disable and enable happening instantly it requires a restart of the os (So it restarts, sees that firmware isn't made for Ubuntu and doesn't load it). 

Any ideas?

---

### Post by yeshmiester on 2008-10-15
Just tried loading the previous kernel and it does the same thing. Now I am really confused. Help!

---

### Post by Ayuthia on 2008-10-15
> **yeshmiester said:**
> I have a broadcom wireless card on my computer and had to load b43fwcutter to get it to work. Every time before this I had to disable/enable the card to get it to work but that wasn't a big issue. 

Today I updated the kernel and now instead of the disable and enable happening instantly it requires a restart of the os (So it restarts, sees that firmware isn't made for Ubuntu and doesn't load it). 

Any ideas?

What do you mean by the firmware isn't made for Ubuntu?

Can you post the results of the following:
```
lshw -C network
uname -a
```

---

