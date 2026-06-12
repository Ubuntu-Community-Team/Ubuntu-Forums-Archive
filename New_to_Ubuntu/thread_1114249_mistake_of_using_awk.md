---
title: "mistake of using awk"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by flylehe on 2009-04-02
Hi,
Here is my code,
```

ids=(1 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75 80 90 100 110 120)
for ((i=0;i<${#ids};i++)); do
   awk '{ print ${ids[${i}]}" "$1; }' > ${TMP} < ./results/$1${ids[${i}]}/test_error.dat
done

```
I got this error 
> 
awk: { print ${ids[${i}]}" "$1; }
awk:          ^ syntax error
awk: { print ${ids[${i}]}" "$1; }
awk:                ^ syntax error
awk: fatal: invalid subscript expression


Could you please explain what mistake I made? Thanks in advance!

---

### Post by Cypher on 2009-04-02
What exactly are you trying to accomplish here? Perhaps if we knew that, we'd have a context for your command and suggest fixes or alternatives..

---

