---
title: "command not found"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by moijdikssekool on 2011-08-24
hello
i have an application in the repertory /home/bouh/documents/k8055, i can see it when i tape 
> cd /home/bouh/documents/k8055
ls
if i tape find -name '*go*', the applicattion go is found
but if i tape sudo ./go or sudo /home/bouh/documents/k8055/go , it says 'sudo: go: command not found'

What is the problem?

---

### Post by sisco311 on 2011-08-24
You need execute permissions to run it:
```
cd /home/bouh/documents/k8055
chmod +x go
./go #or if you have to run it as root: sudo ./go
```

---

### Post by moijdikssekool on 2011-08-24
ok
i'm used to work on a linux (toutou) where there are no rights problem. Is that possible to desactivate all this question of rights?

---

