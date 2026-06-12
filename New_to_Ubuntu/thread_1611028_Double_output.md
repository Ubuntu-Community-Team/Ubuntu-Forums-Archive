---
title: "Double output"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by XeonBloomfield on 2010-11-01
Welcome

How to get double output to console and file in this example:
```
ping -c 4 127.0.0.1
```

When I use ">> ping.txt":
```
ping -c 4 127.0.0.1 >> ping.txt
```
I have got it only to file and in console it blank space...

Regards, XeonBloomfield.

---

### Post by TeoBigusGeekus on 2010-11-01
```
ping -c 4 127.0.0.1| tee ping.txt
```

---

### Post by steviefordi on 2010-11-01
You could try something like:

```
ping -c 4 127.0.0.1 |
while read line
do
echo $line
echo $line >> ping.txt
done
```

---

### Post by steviefordi on 2010-11-01
> ping -c 4 127.0.0.1| tee ping.txt

Fair enough! I guess there are always new commands to learn.

---

### Post by XeonBloomfield on 2010-11-01
Thank you TeoBigusGeekus.
> **TeoBigusGeekus said:**
> ```
ping -c 4 127.0.0.1 | tee ping.txt
```

It works great. 

Problem solved.

---

### Post by TeoBigusGeekus on 2010-11-01
You're welcome. Don't forget to mark the thread as solved.

---

