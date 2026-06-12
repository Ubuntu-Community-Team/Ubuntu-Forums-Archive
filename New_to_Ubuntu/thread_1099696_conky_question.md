---
title: "conky question"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-18
My conky appears to be displaying differently than the conky.conf file suggests.

Where else could conky be getting it's configuration info ?

Where would I find the conkyrc file ?  (search doesn't find it)


thx

---

### Post by m_duck on 2009-03-18
Which config file are you using? The default is in /etc/conky/conky.conf (I think) but that will only be read if you don't have a ~/.conkyrc file in your home directory. Failing that, to be sure, launch conky with the "-c" option and define the configuration file you want to be read, i.e.```
conky -c /path/to/config
```

---

### Post by mistypotato on 2009-03-18
thanks m_duck :KS:KS:KS

---

