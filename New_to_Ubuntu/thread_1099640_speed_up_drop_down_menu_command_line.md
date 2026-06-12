---
title: "speed up drop down menu command line?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by cairnzi on 2009-03-18
hi people, i found a cli ages ago that set the default for the drop down menu's to 0 sec's, but cannot remember where i found it and cannot for the life of me remember what it is, does anybody now what it is? many thanks.

---

### Post by BOZG on 2009-03-18
Try this in the terminal and reboot:

```
echo "gtk-menu-popup-delay = 0" > ~/.gtkrc-2.0
```

---

### Post by cairnzi on 2009-03-18
thats the one! cheers very much. :D

---

### Post by BOZG on 2009-03-19
No problem!

You must be very impatient though :P

---

### Post by D3ath on 2009-03-19
> **BOZG said:**
> No problem!

You must be very impatient though :P
I'm the same way I also add this evertime I change the theme.

---

