---
title: "help please"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by kapi on 2009-02-12
tried opening synaptic manager and keep getting this message:

E:dpkg was interrupted, you must manually run dpkg --configure a to correct the problem

cache ->open() failed . . .please report




can anyone asists please

thanks Kapi

---

### Post by wolfen69 on 2009-02-12
do in terminal:
```
 sudo dpkg --configure -a
```

---

### Post by cariboo on 2009-02-12
This is such a common problem, that any search of google with the words dpkg --configure a, would find more answers to the question than you need. That being said, open a Applications-->Accessories-->Terminal and type:

```
sudo dpkg --configure a
```

You will be asked for your user password, when you type it in, it won't be echoed back, then hit enter.

Jim

---

### Post by kapi on 2009-02-12
Hi done it but it doesnt work

craig@craig-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
craig@craig-laptop:~$ sudo dpkg --configure -a
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
 I hope this helps

thanks 

kapi

---

### Post by kansasnoob on 2009-02-12
> **kapi said:**
> Hi done it but it doesnt work

craig@craig-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
craig@craig-laptop:~$ sudo dpkg --configure -a
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
 I hope this helps

thanks 

kapi

First try:

```
sudo apt-get -f install
```

I wonder what you installed that depends on mysql-server-5.0???? But installing that would be my next suggestion, only I'd use synaptic to watch and see what all it may install or remove to resolve dependencies.

---

### Post by kapi on 2009-02-12
hi synaptic gives me that error message telling me to run dpkg configure a

also the update manager seems to want to download mysql server 5 but then fails and gives me the same dpkg configure a message

really baffled - if you can help I would be grateful indeed

Kapi

---

### Post by sneeks on 2009-02-12
you need to do what it says mate,i will look for an earlier post for u

[http://ubuntuforums.org/showthread.php?t=687595](http://ubuntuforums.org/showthread.php?t=687595)

---

### Post by kapi on 2009-02-12
I have via the terminal, also a message has also stated that cache-> open(),failed.  please report

---

### Post by kapi on 2009-02-12
Thanks everyone for the help. I went to the update manager - selected check for updates then everything seemed to go Ok, except that the apache seemed not to load- will try again

thanks Kapi

---

