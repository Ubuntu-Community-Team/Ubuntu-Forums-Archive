---
title: "arch or $HOSTFILE?????????"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by @rizz on 2010-05-28
Hi all,

   I have a small question.....

  i ran two commands and both gives me two different answer for the same question....

  ```
$>arch
$> i686
``` 

and then if i ran the the following command  it tells me something else

          ```
$> echo $PATH
$>i486
```   whom do i belive???????????:dazed:

---

### Post by cariboo on 2010-05-28
I think probably the best way to find what architecture you are running is to use :

```
cat /proc/cpuinfo
```

The result you got from:

```
echo $PATH
```

is weird, I get the following output running the command:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by Zemblan on 2010-05-28
$PATH is an environmental variable which specifies those directories which the shell searches in when you enter a command. For example, if you enter 'ls' the shell searches those directories in that variable for executable called 'ls' so that you don't have to enter the full directory name each time. It has nothing to do with the architecture of your cpu. So something has gone awry with your setup somehow. Unless you have altered your config files in some way simply closing that shell and opening a new one will allow you to get a proper result from 'echo $PATH.

---

