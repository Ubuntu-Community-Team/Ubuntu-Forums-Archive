---
title: "Can I force install a package?"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by DaveGiant on 2010-02-25
I am trying to get php5.3 package from dotdeb...

However, it has some dependencies that to my untrained eye just seem dumb! Example libicu38

Aptitude says this is unavailable... I have libicu40... surely this is 2 versions higher than what is expected and thus it means the dependency..

Can I do anything about this?

---

### Post by shihkster1015 on 2010-02-25
i'm not sure about this but try
```
 sudo dpkg -i *filename*
```


please correct me if i'm wrong

---

### Post by Bachstelze on 2010-02-25
> **DaveGiant said:**
> 
Aptitude says this is unavailable... I have libicu40... surely this is 2 versions higher than what is expected and thus it means the dependency..

It does not. If a program expects a given version of a library, you must give it that exact version. It's not "38 or higher", it's "38, period".

You can get libicu38 from the Jaunty repositories. Either download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) or add them to your sources.list.

---

### Post by DaveGiant on 2010-02-25
Is this what you wanted me to do?

> jason@jason-laptop:~$ sudo dpkg -i libicu38
[sudo] password for jason: 
dpkg: status database area is locked by another process
jason@jason-laptop:~$ sudo dpkg -i libicu38
dpkg: error processing libicu38 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libicu38
jason@jason-laptop:~$ 


---

### Post by shihkster1015 on 2010-02-25
if you have synaptics opened, close it

---

### Post by DaveGiant on 2010-02-25
> **Bachstelze said:**
> It does not. If a program expects a given version of a library, you must give it that exact version. It's not "38 or higher", it's "38, period".

You can get libicu38 from the Jaunty repositories. Either download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) or add them to your sources.list.

Thanks for your help, could you tell me the url to put in the sources list?

---

### Post by Bachstelze on 2010-02-25
> **DaveGiant said:**
> Thanks for your help, could you tell me the url to put in the sources list?

Something like:

```
deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb http://security.ubuntu.com/ubuntu jaunty-security main
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main

```

Remember to just *add* those lines, don't replace anything in what you already have. Then do

```
sudo apt-get update
sudo apt-get install libicu38
```

---

