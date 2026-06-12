---
title: "driver numbering and partitons"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by rfbeck on 2009-01-17
I have a 1TB drive with Win XP and a smaller 250GB drive with Ubuntu. How do I know what drive Ubuntu considers itself on 0, or 1? 
And how can I find out what partitions it has given itself since even though I have a dual boot system, and my operating systems are on separate drives? Thanks for the help.

---

### Post by taurus on 2009-01-17
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by rfbeck on 2009-01-17
That's exactly what I needed to know. Thanks.
______
Robert

---

