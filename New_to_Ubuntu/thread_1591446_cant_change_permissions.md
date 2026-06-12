---
title: "cant change permissions"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by LeitoSR on 2010-10-09
hello,

i have a little problem adding some fonts to be able to read old .doc files create by word 97

i read some where that i have to copy the old fonts to the dir in the pictures but i found that im not able to..

i tried to check why so i found that im not the Administrator it was Custom so i changed it to Administrator and tried again and its the same.

what to do to copy or edit in subdirectories in root directory ?

[http://img515.imageshack.us/img515/8563/screenshota.png](http://img515.imageshack.us/img515/8563/screenshota.png)

---

### Post by e79 on 2010-10-09
In a terminal type :
```

gksu nautilus

```Nautilus will then open in 'root' mode allowing you to copy your fonts. Be cautious of what you do while in this mode since you can damage your system if you don't know what you're doing.

Hope this helps

---

### Post by jkzubu on 2010-10-09
Thank you e79!

Your simple post helped me solve a similar problem related to permissions for an extra drive!

JK

---

### Post by e79 on 2010-10-09
My Pleasure  :P

---

### Post by LeitoSR on 2010-10-14
Thnx alot, it worked perfectly. :)

---

