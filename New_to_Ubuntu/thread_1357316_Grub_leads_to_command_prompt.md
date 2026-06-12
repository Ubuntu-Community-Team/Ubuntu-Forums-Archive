---
title: "Grub leads to command prompt"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by mancroft on 2009-12-17
Using Koala.

I sometimes get an error when starting Ubuntu.

Instead of going to the normal coloured screen with the login box, it goes to a command prompt which says "john desktop login".

Is there a command to get from this command prompt to the Ubuntu desktop without restarting the computer?

---

### Post by nothingspecial on 2009-12-17
```
startx
```

or
```

sudo service gdm start
```

---

### Post by pi4r0n on 2009-12-17
If I understand it correctly you just need to type **startx** and press Enter

---

### Post by mancroft on 2009-12-17
Phew, nothingspecial, that was quick!

Much obliged.

---

