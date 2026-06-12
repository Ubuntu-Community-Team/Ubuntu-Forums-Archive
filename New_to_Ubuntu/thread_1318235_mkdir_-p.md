---
title: "mkdir -p"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by genetik on 2009-11-07
what does the -p mean/do?

---

### Post by oldos2er on 2009-11-07
**man mkdir** has the answer: -p, --parents
 no error if existing, make parent directories as needed

---

### Post by SuperSonic4 on 2009-11-07
means create the parent directories if they don't exist

---

### Post by nothingspecial on 2009-11-07
So if you want to make a directory called wow in a directory blah in a directory blag........

you go ```
mkdir -p blag/blah/wow
```

instead of

```
mkdir blag
mkdir blag/blah
mkdir blag/blah/wow
```

---

