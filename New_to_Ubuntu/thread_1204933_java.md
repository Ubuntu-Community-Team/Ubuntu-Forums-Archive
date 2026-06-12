---
title: "java"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by mosquetero on 2009-07-05
Hi everyone!

I am trying to install a program which needs the command java but I don't know where can I get it. If I type it on the terminal it says that "java" can be found in the following packages, but there are 7 and I wanted to ask you, my wise friends, which one is exactly the one I need.

Thank you in advance

---

### Post by credobyte on 2009-07-05
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by mosquetero on 2009-07-05
Thanks, but it doesn't work, I get this: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

Do you have any idea of how to solve it?

Thanks again

---

### Post by oldos2er on 2009-07-05
Make sure you have the multiverse repository enabled (System, Administration, Software Sources).

---

### Post by credobyte on 2009-07-05
```
sudo aptitude search sun-java6
```

Can you post the output of this command ?

---

