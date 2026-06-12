---
title: "Terminal Commands Questions"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by jmschuaquico on 2010-12-05
Hi!

I'm trying to familiarize myself with Terminal Commands in Ubuntu. (I am learning shell scripting)
Here are my questions...

how do i count the number of subdirectories in the current directory?
how do i count the files in the current directory?

TIA!

---

### Post by alend on 2010-12-05
# show number of directories + files
ls | wc

---

### Post by DaithiF on 2010-12-05
some examples:

```
num_dirs=$(find . -mindepth 1 -maxdepth 1 -type d | wc -l)
num_dirs=$(ls -d */ | wc -l)
num_files=$(find . -maxdepth 1 -type f | wc -l)

```

---

### Post by sisco311 on 2010-12-05
The number of subdirectories is the number of hard links to the dir -2:
```
echo $(( $(ls -dl path/to/dir | awk '{print $2}') - 2 ))
```
or
```
echo $(( $(stat -c '%h' path/to/dir) - 2 ))
```

---

### Post by jmschuaquico on 2010-12-05
Thanks!

what about listing all the files in the current directory whose size is equal to, say, 100KB?
(there will be more questions ^_^) THanks!

---

### Post by sisco311 on 2010-12-05
Is this your homework? 

See:
```
man find
```

---

