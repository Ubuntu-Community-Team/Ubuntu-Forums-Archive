---
title: "terminal command to check memory [Ram] ?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mickeyjoe on 2009-12-27
How can I check how much memory [Ram] my computer has [or can still take] ?

---

### Post by falconindy on 2009-12-27
'free -m' shows both physical and virtual in a reasonably straightforward manner.

---

### Post by whitethorn on 2009-12-27
To view your ram info

```

cat /proc/meminfo
top

```

To find out how much ram your computer can handle.  You need to google either your computer model (laptop) or your motherboard (desktop pc).

---

