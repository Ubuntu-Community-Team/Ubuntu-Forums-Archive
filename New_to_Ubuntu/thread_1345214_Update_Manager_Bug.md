---
title: "Update Manager Bug?"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by donaldshelton on 2009-12-03
E: Type deb is not known in line 53 in resource list /etc/apt/sources.list,
E: The list of sources could not be read"..

How do I resolve this problem???

I have opened the sources.list file, but I don't know which "deb" the error is referring to.  Is there a way for line #s to be shown?

(I always sound so stupid when posting questions, so please, bear with me!)

---

### Post by cariboo on 2009-12-03
Open /etc/apt/sources.list in gedit, press Alt-F2 and type:

```
gksudo gedit /etc/apt/sources.list
```

once gedit is open go to Edit-->Preferences and enable line numbering, then just check line 53 for a syntax error.

---

### Post by donaldshelton on 2009-12-03
Well, as usual, the solution was simple.

Thanks again for the assistance!!!!!

Don

---

