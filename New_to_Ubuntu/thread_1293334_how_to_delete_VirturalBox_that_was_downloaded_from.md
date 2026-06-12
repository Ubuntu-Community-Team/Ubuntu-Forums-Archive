---
title: "how to delete VirturalBox that was downloaded from websight?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-16
i cant do it through terminal and synaptic cause i dident get it through them. so how do i get rid of it?

---

### Post by OpenGuard on 2009-10-17
```
dpkg -l | grep virtualbox

```

Additionally, you can try vbox ( I'm not 100% sure how it's called ). If it finds something, take the package name ( <name>_<weird-stuff> ) and use -r to remove it.

```
dpkg -r <package>
```

---

