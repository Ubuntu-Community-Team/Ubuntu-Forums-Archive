---
title: "Batch zip with rules"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by brujadeleste on 2010-11-15
Hi everyone.
I have a folder with many many files which should be filed in groups according to the beginning of their names. 

Eg:
P10001 Form
P10001 Budget
P10002 Form 3
P10002 Budget
P10002 Schedule

I want the two files beginning with P10001 in one zip file and the three files beginning with P10002 in another zip file.

Thanks in advance!

---

### Post by marshmallow1304 on 2010-11-16
```
for i in {1..100}
do
    zip P1000$i.zip P1000$i*
done
```


Assuming we go from P10001 to P1000100.

---

