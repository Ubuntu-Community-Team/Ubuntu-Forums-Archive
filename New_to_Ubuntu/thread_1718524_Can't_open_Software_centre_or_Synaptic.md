---
title: "Can't open Software centre or Synaptic"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by idle1 on 2011-03-31
Just tried to open Ubuntu software centre and it would'nt open... So I tried to open Synaptic instead and that won't open either. Just tried to open update manager and that won't open either.

When I run software centre from the terminal I get 'Segmentation fault'

When I try to open Synaptic I also get 'Segmentation fault', and the same for update manager

Any ideas how to fix this?

---

### Post by wolfen69 on 2011-03-31
Try:
```
sudo rm /var/cache/apt/*.bin
```

---

### Post by idle1 on 2011-03-31
Nice one Wolfen - works like a charm.

Many thanks :)

---

