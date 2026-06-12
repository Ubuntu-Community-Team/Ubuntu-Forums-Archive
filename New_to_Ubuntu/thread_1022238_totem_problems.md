---
title: "totem problems"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-12-26
totem wont start 
heres the output
```
spence@spence-desktop:~$ totem
totem: /lib/tls/i686/cmov/libresolv.so.2: version `GLIBC_2.9' not found (required by /lib/libkrb5.so.3)

```

---

### Post by nhasian on 2008-12-26
are you running Hardy, Intrepid, or a prerelease version of Jaunty?

---

### Post by wolfen69 on 2008-12-26
just try reinstalling from scratch. go to synaptic and completely remove totem. then open terminal and: 
```
sudo apt-get clean
```then
```
sudo apt-get autoremove
```then 
```
sudo apt-get install totem
``` any dependency issues should now be resolved.

---

### Post by SpenceMakesSense on 2008-12-26
well i found out it was giving me that output for a majority of my programs so I reinstalled ubuntu and everything is good thanks for the help though

---

