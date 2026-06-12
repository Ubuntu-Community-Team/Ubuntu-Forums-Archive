---
title: "Shared Memory"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by green_gal on 2007-07-31
How do i create shared memory with malloc?

---

### Post by PaulFr on 2007-07-31
**[http://tldp.org/LDP/lpg/node65.html](http://tldp.org/LDP/lpg/node65.html)** should help - malloc allocates on heap, what you need is the shmxxx functions.

---

