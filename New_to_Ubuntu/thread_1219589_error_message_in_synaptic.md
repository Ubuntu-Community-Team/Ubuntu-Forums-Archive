---
title: "error message in synaptic"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by misswham on 2009-07-21
I am trying to go to synaptic and this is the message I am getting

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



what do i do?

---

### Post by misswham on 2009-07-21
i figured it out now it says i have a broken file go to filter to find it.  what does that mean?

---

### Post by NovaAesa on 2009-07-21
You will need to open a terminal window (Apps->Accessories->Terminal) and type ```

dpkg --configure -a

```
and then press enter. Post back whatever message it says.

---

