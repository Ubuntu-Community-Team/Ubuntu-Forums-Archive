---
title: "Help: lost internet connection all of a sudden -&gt; connection refused"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by raul_ on 2007-04-28
when I type

```
host www.google.com
```

i get

```

Host www.google.com not found: 5(REFUSED)

```

---

### Post by taoufix on 2007-04-29
can u ping the nameservers in ur  /etc/resolv.conf  ?

---

### Post by raul_ on 2007-04-29
Sorry i forgot to flag this one as resolved. 

Turns out that when i connected to the internet in my college, it messed up my resolv.conf file, i had to change the nameservers. But you were in the right track :)

---

