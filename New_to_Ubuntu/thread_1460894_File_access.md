---
title: "File access"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-23
I believe that there is a command that one can use on a program to see all of the files that program accesses and where the compiler thinks they are.


What is this Linux command?

Newport_j

---

### Post by arrrghhh on 2010-04-23
> **newport_j said:**
> I believe that there is a command that one can use on a program to see all of the files that program accesses and where the compiler thinks they are.


What is this Linux command?

Newport_j

It's not a straight command (at least I don't know one...)

Read [here](http://www.cyberciti.biz/faq/howto-linux-get-list-of-open-files/) - uses a combination of ps and ls.

Oh, and lsof is a great one as well, which is mentioned at the end of that post. :D

---

### Post by iponeverything on 2010-04-23
```
sudo lsof -p <process-pid>
```

---

### Post by talonmies on 2010-04-24
> **newport_j said:**
> I believe that there is a command that one can use on a program to see all of the files that program accesses and where the compiler thinks they are.


ldd

---

