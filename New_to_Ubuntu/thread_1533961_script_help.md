---
title: "script help"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by scratchr on 2010-07-18
this script wont work
```
#!/bin/bash
read -p "file 1:" a
read -p "file 2:" b
read -p "out:" c
cat $a $b >> $c
```

---

### Post by lkjoel on 2010-07-18
> **scratchr said:**
> this script wont work
```
#!/bin/bash
read -p "file 1:" a
read -p "file 2:" b
read -p "out:" c
cat $a $b >> $c
```
What are you trying to do?
Try:
```
 read -p "file 1:" a
read -p "file 2:" b
read -p "out:" c
cat $a  >> $c
cat $b >> $c
```

---

### Post by scratchr on 2010-07-22
nope, it did not work.
It was to add two files into one.

---

### Post by DaithiF on 2010-07-22
Hi, works for me.  though the >> is not necessary if you are creating the new file, just > is fine because the cat will already have concatenated the contents of both files into a single stream.

as to why its not working for you ... spaces in the filenames?  if so use "" marks:
cat "$a" "$b" > "$c"

---

