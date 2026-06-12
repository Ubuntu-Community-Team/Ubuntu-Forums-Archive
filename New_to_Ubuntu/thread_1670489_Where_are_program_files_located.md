---
title: "Where are program files located?"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by Shadow21 on 2011-01-19
Where is the actual executable type file for a program located? 

I'm needing to supply the Folding@Home location to FahMon (Folding@Home GUI).

---

### Post by Tony Flury on 2011-01-19
open a terminal and type 

```

which FahMon

```

---

### Post by Shadow21 on 2011-01-19
> **Tony Flury said:**
> open a terminal and type 

```

which FahMon

```

I actually need to look for foldingathome-smp which isn't a command so using 

```
which fodlingathome-smp
```

doesn't work.

---

### Post by ppv on 2011-01-19
The spelling of folding isn't what you would want in the code posted...is that why you are seeing that the command isn't working.

---

### Post by JC Cheloven on 2011-01-19
Programs (in binary executable form) are usually in /usr/bin if it's something you installed, or in /bin is it's something system related.

Cheers

---

### Post by Shadow21 on 2011-01-19
I was finally able to find the Folding@Home directory in /opt.

---

