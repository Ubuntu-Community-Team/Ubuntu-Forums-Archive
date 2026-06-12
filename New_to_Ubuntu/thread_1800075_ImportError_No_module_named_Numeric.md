---
title: "ImportError: No module named Numeric"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Saad Bin Ahmed on 2011-07-08
Hi, 
If somebody knows about the following error then please guide me how can I solve it.

File "arabic_offline.py", line 3, in <module>
    from Numeric import *
ImportError: No module named Numeric

Thanks in advance,

---

### Post by painejake on 2011-07-19
```
sudo apt-get install python-numeric
```

:)

---

### Post by ephan on 2011-10-30
This doesn't work in Ubuntu Oneiric, this package doesn't seem to be in the repos here, and I also couldn't build it from source.

---

### Post by gmargo on 2011-10-30
According to this Wikipedia article, NumPy is the successor to Numeric.  You may be able to get by with replacing "Numeric" with "NumPy".

[https://secure.wikimedia.org/wikipedia/en/wiki/NumPy](https://secure.wikimedia.org/wikipedia/en/wiki/NumPy)

The python-numpy package description includes this:
> 
 Numpy replaces the python-numeric and python-numarray modules which are
 now deprecated and shouldn't be used except to support older
 software.


---

### Post by sd08154711 on 2011-12-10
To complete the request:

Replace "Numeric" with "numpy" (low letters)

This helped me getting WeatherScreenlet to work again in oneiric.

---

