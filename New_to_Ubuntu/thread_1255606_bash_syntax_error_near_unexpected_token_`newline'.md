---
title: "bash: syntax error near unexpected token `newline'"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by pantmerchant on 2009-09-01
Hello all. I'm running  Ubuntu Server and am having problems running a .sh script trying to build a Open GTS Server.

the command is 

bin/initdb.sh -rootUser=<rootUser> -rootPass=<rootPass>

The script is supposed to create a new mysql database. When i run the command i get..

-bash: syntax error near unexpected token `newline'

I've tried running it as sudo and my user and i get the same thing.

tia

---

### Post by DaithiF on 2009-09-01
do root user or password contain the sequence \n ?

---

### Post by pantmerchant on 2009-09-01
> **DaithiF said:**
> do root user or password contain the sequence \n ?
No, there's an n but no \n in the rootUser / rootPass and just to be certain i changed the mysql root password to something without an n and got the same error.

---

### Post by DaithiF on 2009-09-02
Hmm ...  ok, wild guess, when it says 
```
bin/initdb.sh -rootUser=<rootUser> -rootPass=<rootPass>
```

are you typing:
```
bin/initdb.sh -rootUser=<rootUser> -rootPass=<rootPass>

```or
```
bin/initdb.sh -rootUser=rootUser -rootPass=rootPass
```

(its the second one that you need -- the angle brackets are there as placeholders, they're not meant to be typed)

---

### Post by pantmerchant on 2009-09-02
> **DaithiF said:**
> Hmm ...  ok, wild guess, when it says 
```
bin/initdb.sh -rootUser=<rootUser> -rootPass=<rootPass>
```

are you typing:
```
bin/initdb.sh -rootUser=<rootUser> -rootPass=<rootPass>

```or
```
bin/initdb.sh -rootUser=rootUser -rootPass=rootPass
```

(its the second one that you need -- the angle brackets are there as placeholders, they're not meant to be typed)
doh! taking out the angle brackets did it.

thanks!

---

### Post by admasb on 2012-09-19
Solved mine too Thank U.

---

