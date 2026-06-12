---
title: "Nautilus problems"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by airplanesimen on 2011-02-09
Im trying to open a folder in ubuntu, and it appears down on the bar, but it doesnt start, and it dissapears. when im restarting ubuntu, it says "can't restart (nautilus not responding)" anyone know how to help me?

---

### Post by Frogs Hair on 2011-02-09
You could try restarting Nautilus using :```
nautilus -q 
```

---

### Post by airplanesimen on 2011-02-09
> **Frogs Hair said:**
> You could try restarting Nautilus using :```
nautilus -q 
```
 i have tried that one, and "pkill nautilus". but the same problem... Is it to any help that it is not responding when im restarting my computer? can nautilus be some kind of corrupted? in that case, how to reinstall it (if its possible?)

---

### Post by Luinar on 2011-02-09
How about using ```
killall nautilus
``` to end the process?

---

### Post by Frogs Hair on 2011-02-09
You could mark Nautilus for reinstallation from System > Administration > Synaptic Package Manager. Use the search filter to locate Nautilus and right click on the line , mark and apply. Be sure to have backup beforehand.

---

### Post by matt_symes on 2011-02-09
Hi

Does running this in a terminal return anything useful ?

```
nautilus -c
```

Kind regards

---

### Post by airplanesimen on 2011-02-09
Yes, thanks a lot, my problem is svolved by reinstalling it:P :guitar:

---

