---
title: "proplem with installing from tar.gz"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Ghost M.D on 2009-02-07
Hi all

I want to install teeworlds game the tar.gz the only I saw in the site

I tried to install it but it go wrong 

this is what I done in terminal after I extract it in home 

```
ahmad@ahmad-laptop:~$ cd teeworlds-0.5.1-linux_x86
ahmad@ahmad-laptop:~/teeworlds-0.5.1-linux_x86$ ./configure
bash: ./configure: No such file or directory
ahmad@ahmad-laptop:~/teeworlds-0.5.1-linux_x86$ make
make: *** No targets specified and no makefile found.  Stop.
ahmad@ahmad-laptop:~/teeworlds-0.5.1-linux_x86$ sudo make install
[sudo] password for ahmad: 
make: *** No rule to make target `install'.  Stop.

```

am I do something wrong or not 

& this is the site for the game

[http://www.teeworlds.com/]("http://www.teeworlds.com/")

---

### Post by oldos2er on 2009-02-07
It's precompiled binaries. From within the teeworld directory, type "./teeworlds" without the quote marks.

---

### Post by Ghost M.D on 2009-02-07
It works thank you very much

---

