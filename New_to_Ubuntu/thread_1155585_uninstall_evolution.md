---
title: "uninstall evolution"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-05-10
I want to unistall evolutiton.  Whats the best way to go about doing so without crashing my system?

---

### Post by jaithehulk on 2009-05-11
IMHO, The best way wld be to remove it from synaptic package manager...it will surely not harm ur system...

---

### Post by pytheas22 on 2009-05-11
Yes, just remove the package named 'evolution' using Synaptic or Add/Remove Programs, or type:
```

sudo apt-get remove evolution
```

The packages that are installed by default in Ubuntu and depend on 'evolution' (there are only three of them) can be removed without causing any problems.

---

### Post by trinidadflores on 2009-05-11
what all do i have to mark for the evolution program.  I want to make sure that i have it all.

---

### Post by pytheas22 on 2009-05-11
You only need to mark the package named 'evolution'.  The others should be removed automatically because they depend on that package.

---

