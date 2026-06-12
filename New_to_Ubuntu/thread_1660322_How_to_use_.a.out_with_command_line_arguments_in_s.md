---
title: "How to use ./a.out with command line arguments in shell script?"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by ajaybidari on 2011-01-05
cc -fopenmp lifeopenmp.c
for((i=1;i<500;i+100))
do
 ./a.out 20 $i
done


Above is a small script I am trying to write to run lifeopenmp.c with two command line arguments. I have to execute ./a.out multiple times with two command line arguments, the first one being a constant and a second one is a variable.I am not able to give the 2nd arg. Help me how to specify the 2nd arg.


Thanks.

---

### Post by Stephen Morgan on 2011-01-05
for((i=1;i<500;i+100))
do
 ./a.out 20 $i
done

try

for ((i=1;i<500;i+=100)); do
 ./a.out 20 $i
done

The += sign, as C and awk users will know, means, in this case, i = i + 100. i + 100 doesn't mean anything. The amended script should work.

---

