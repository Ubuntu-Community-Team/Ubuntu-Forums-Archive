---
title: "NOOB! question about moving files"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by maxxerific on 2009-11-24
okay - i understand the basics of mv. 
can't seem to find documentation for this case:

i'm in /dirA/dirB  

test file TEST is in dirA

i want to move TEST from dirA --> dirB
but without specifying absolute file path

pwd
/dirA/dirB

mv ../TEST   ???? 

what are the question marks!!!!

i feel like an idiot. i've been working on this for like 30 minutes

---

### Post by lewisforlife on 2009-11-24
If I understand correctly.  You want to move TEST from dirA to dirB.  First, cd into dirB.  Then:

```
mv ../TEST .
```

Note that you can type the first couple of letters of the file name TEST, then hit the tab button and it will complete TEST for you.  You can also do this with the directories.

Thanks,

David

---

### Post by Cheesemill on 2009-11-24
You can use:
```
mv ../TEST .
```

. means the current directory

---

### Post by maxxerific on 2009-11-24
thansk dave - thats exactly what i was looking for :)

---

### Post by maxxerific on 2009-11-24
ah! 
   thanks! 
    
so easy it makes my brain hurt.

---

