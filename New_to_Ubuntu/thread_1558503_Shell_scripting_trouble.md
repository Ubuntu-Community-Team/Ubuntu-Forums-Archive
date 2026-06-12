---
title: "Shell scripting trouble"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by nebu on 2010-08-22
I want to pass the output of
```
 grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1}'
```
to a script run.sh as its second argument ie
```
 ./run.sh pkg <argument>
```

what i am doing now is
```
 grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1}'| xargs ./run.sh pkg
```

but this is not working! what am i doing wrong??

---

### Post by Brandon Williams on 2010-08-22
If the output from the command is just supposed to provide arguments for run.sh, there's no need to use xargs. You can just use bash command substitution.

If you want the output to provide multiple white-space separated tokens:
```
./run.sh pkg $(grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1}')
```

If you want one single argument, then quote the command substitution expression:

```
./run.sh pkg "$(grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1}')"
```

If it still doesn't work, then run your script with the -x argument to get debugging output so you can figure out what's going wrong, as in:

```
bash -x ./run.sh pkg $(grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1}')
```

---

### Post by nebu on 2010-08-22
no.... i want every line of the output to got to a different ./run.sh so i was using the xargs!

---

### Post by vijayanand_sodadasi on 2010-08-22
If every line of output should go to separate instance of run.sh, then you can do it with a bit of shell scripting as follows:

```
for arg2 in $(grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1}')
do
   ./run.sh pkg $arg2
done
```

---

### Post by Brandon Williams on 2010-08-22
> **nebu said:**
> no.... i want every line of the output to got to a different ./run.sh so i was using the xargs!

Ah ... well, in that case, you should be using the '-L max-lines' option for xargs, or the for loop quoted above.

---

### Post by bilkay on 2010-08-22
Another way:

```
grep -P "^[a-zA-Z0-9:]+\s+package" ctags_output.proc | awk '{print $1} | while read x
do
     ./run.sh pkg $x
done
```

---

### Post by David Andersson on 2010-08-22
Option **-l** to xargs will run command once for each line in the input.
Option **-n1** to xargs will run command once for each word in the input.
I think any would work in this case.

---

