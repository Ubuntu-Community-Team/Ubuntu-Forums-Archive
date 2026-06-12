---
title: "the test command"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by josephmills on 2011-05-23
why is it not telling me 0 or 1 ? I think that is has to do with the bold part  
```
test 123 -lt 124 **; echo #? **
``` thanks

---

### Post by matt_symes on 2011-05-23
Hi

> **josephmills said:**
> why is it not telling me 0 or 1 ? I think that is has to do with the bold part  
```
test 123 -lt 124 **; echo #? **
``` thanks

Hope your well Joseph.

Try this instead.

```
test 123 -lt 124 **; echo $? **
``` 

```
clfs@matthew-laptop:/mnt/clfs/texinfo-4.11$ test 123 -lt 124 ; echo **$?** 
0
clfs@matthew-laptop:/mnt/clfs/texinfo-4.11$ 
```

**$?** is the returned value form the last command.

Kind regads

---

### Post by josephmills on 2011-05-23
SOLVED it is ```
123 -lt 124 ; echo $? 
``` feels great thanks MATT I did not see you there you rock man

---

