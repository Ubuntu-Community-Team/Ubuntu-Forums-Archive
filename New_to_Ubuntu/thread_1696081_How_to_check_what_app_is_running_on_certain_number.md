---
title: "How to check what app is running on certain number?"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by newn on 2011-02-26
Hi. How can I check what app is using certain number? For example 422, 8645, 45756, etc... I don't know how they are called.

---

### Post by doas777 on 2011-02-26
well, you might mean Process IDs (PID) or network Port numbers. 

for PIDs, run 
```

top

```

to see a list of running processes with their pid.

for Network ports, run
```

sudo netstat -ntlup

```
to see a list of ports with a service listening on them. the last column is the name of the process listening on that port.

---

### Post by newn on 2011-02-26
Thanks.

---

