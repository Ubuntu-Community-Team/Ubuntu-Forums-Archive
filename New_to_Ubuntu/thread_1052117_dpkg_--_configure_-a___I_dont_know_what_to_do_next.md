---
title: "dpkg -- configure -a ?  I dont know what to do next ."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by minkynink on 2009-01-27
Hello all . 
I have just received this error message when i was trying to install a ubuntu tweak deb package .
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  E: _cache->open() failed, please report.

Can someone please help me with what i am meant to do next ?

Im a noob so a step by step list of what to do will be very gratefully appreciated .

Thanks

Mink

---

### Post by OffAxis on 2009-01-27
just type that into the command line

```
sudo dpkg --configure -a
```

---

### Post by Tim Sharitt on 2009-01-27
Open a terminal by going to Applications > Accessories > Terminal and enter
```
sudo dpkg --configure -a
```
Then enter your password when prompted.

---

### Post by rafaelsousa on 2009-01-27
What happens when you 
```
sudo dpkg --configure -a
```
???

---

### Post by bgerlich on 2009-01-27
Have you tried manually running "dpkg --configure -a" by typing ```
sudo dpkg --configure -a
``` in the console ? :)

---

### Post by bgerlich on 2009-01-27
Heh, four exactly the same answers in less than a minute ;)

---

### Post by rafaelsousa on 2009-01-27
You can try a

```
sudo apt-get install -f
```

either.

---

### Post by minkynink on 2009-01-27
Ok . I think ive found it .

just ran 
sudo dpkg --configure -a

Im learning .

---

### Post by minkynink on 2009-01-27
Thanks all .

---

### Post by rafaelsousa on 2009-01-27
bgerlich: Isn't wonderful how cool are ubuntu users?! Immediatly everyone replied!!! hehehehe

---

### Post by jerome1232 on 2009-01-27
> **rafaelsousa said:**
> What happens when you 
```
sudo dpkg --configure -a
```
???

From the man page of dpkg (type man dpkg to view it your self)

```
dpkg --configure package ... | -a | --pending
    Reconfigure an unpacked package. If -a or --pending is given instead of package, all unpacked but unconfigured packages are configured.

    Configuring consists of the following steps:

    1. Unpack the configuration files, and at the same time back up the old configuration files, so that they can be restored if something goes wrong.

    2. Run postinst script, if provided by the package. 
```

---

### Post by minkynink on 2009-01-27
"Don't let your mind wander -- it's too little to be let out alone."


This is So true of me today !

---

