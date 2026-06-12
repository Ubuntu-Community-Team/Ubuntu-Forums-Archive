---
title: "List items in a PPA?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-29
How would i go about listing items in a PPA? For example lets say i add the docky PPA:

```
sudo apt-get-repository ppa:docky-core/stable
```

Once added how do i figure out what is in that PPA? What i mean is lets say i wanted to run 

sudo apt install docky, but the file name is docky2.1.  How would i know its called docky2.1?

Thanks

---

### Post by mikewhatever on 2010-12-29
You could search, for example, **apt-cache search docky** and all related packages should be listed.

---

### Post by hunter99507 on 2010-12-29
Is their an alternative way to figure out exactly what is in that package?

---

### Post by mikewhatever on 2010-12-29
What do you mean, what package?

---

### Post by hunter99507 on 2010-12-29
Any package. If i add any ppa, i would like to know how to list the files in the PPA that i could install. So i know if i add the docky PPA, to install docky i would need to 

sudo apt install docky

but how do i list the files in ppa:docky-core/stable?

---

### Post by mc4man on 2010-12-29
One way would be to open synaptic package manager  - click on the 'origin' tab, choose the ppa and it will list all packages available from that ppa
(software center can do the same in maverick

---

### Post by hunter99507 on 2010-12-29
> **mc4man said:**
> One way would be to open synaptic package manager  - click on the 'origin' tab, choose the ppa and it will list all packages available from that ppa
(software center can do the same in maverick

That answered my question. Thank you

---

