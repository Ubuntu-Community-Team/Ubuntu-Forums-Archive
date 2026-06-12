---
title: "Searching repository via terminal"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by coolbrook on 2009-08-01
How can we do a keyword search on the repository without opening Synaptic?

---

### Post by andrew.46 on 2009-08-01
Hi coolbrook,

> **coolbrook said:**
> How can we do a keyword search on the repository without opening Synaptic?

Well, if you were searching for slrn packages you would try:

```

sudo apt-get update
apt-cache search slrn

```

and if you were searching for the 'dev'libraries of slrn you could modify this a little"

```
apt-cache search slrn | grep 'dev'
```

All the best,

Andrew

---

### Post by RomeReactor on 2009-08-01
Hi. You could also try using:
```
aptitude search keyword
```
For example:
```
aptitude search nautilus
```

---

### Post by coolbrook on 2009-08-01
Thanks dudes 8-)

---

### Post by mcduck on 2009-08-01
..and, after you've found a package you can check it's detailed information with this command:

```
apt-cache show packagename
```

---

