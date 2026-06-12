---
title: "Changing permissions"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Benbow on 2009-08-30
I know how to change permissions - properties/permissions etc but I have several partitions on my 500gb hard drive and some of these partitions are unavailable due to the whole permissions section being greyed out.

I have always been less than average in technical comprehension (I think!) so can anyone explain what I should do to put this right?

Thanks.

---

### Post by credobyte on 2009-08-30
This should help:
```
sudo chown -R user:group /mount/point

```
[COLOR=Gray]Replace user:group with what you have there.[/COLOR]

Otherwise:
```
sudo chmod -R ??? /mount/point
```[COLOR=Gray]Replace ??? with what you need ( 655, 755, 777, ???, etc. ).[/COLOR]

---

### Post by Benbow on 2009-08-30
Thanks Credobyte, I think that you have solved my problem.:P

---

