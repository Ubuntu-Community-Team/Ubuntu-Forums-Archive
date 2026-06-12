---
title: "can someone write me an &quot;update then switch off&quot; script so I can go to sleep"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-06-25
I mean it, my slow *** connection means that I'll be sat here for two hours waiting for the 198mb download

Can someone tell me(or do it for me) how to make a script that will do the update, then shut down the computer.

thanks

---

### Post by Colo2 on 2010-06-25
what harm would it do to keep the PC on over night?

I do, especially when there's big downloads.

---

### Post by JamesParnell on 2010-06-25
What harm? WHAT HARM!!!

you don't know my girlfriend :D

---

### Post by fremantle on 2010-06-25
what wrong with her?

---

### Post by S.R on 2010-06-25
[http://www.computerhope.com/unix/ushutdow.htm](http://www.computerhope.com/unix/ushutdow.htm) 

Yay for google

---

### Post by JamesParnell on 2010-06-25
ah, she'd kill me if I left it on all night :P. 

still, is my script thingy possible?

---

### Post by JamesParnell on 2010-06-25
google led me to the "ideas" page XD

---

### Post by tgalati4 on 2010-06-25
sudo su
apt-get update &&  apt-get -y upgrade &&  pm-suspend
apt-get install new-gf

---

### Post by JamesParnell on 2010-06-25
Anyway,great stuff, thanks :)

at 2:38am....g'Night!.

---

### Post by JamesParnell on 2010-06-25
Anyway,great stuff, thanks :)

at 2:38am....g'Night!.

---

### Post by k3lt01 on 2010-06-25
> **tgalati4 said:**
> apt-get install new-gf:lolflag:

---

### Post by Colo2 on 2010-06-25
goodnight to you too ;) 3:49 here.

---

### Post by ibuclaw on 2010-06-25
In the file /etc/apt/apt.conf

Something like:
```

DPkg
{
    Pre-Invoke  { "shutdown -c" };
    Post-Invoke { "shutdown -h +20" };
};

```
May work.

Not too sure tbh... :)

---

### Post by NightwishFan on 2010-06-26
Why not such make an shell script to do:
```
sudo aptitude update && sudo aptitude -y safe-upgrade && sudo init 0
```

Does "init 0" need sudo?

---

### Post by ibuclaw on 2010-06-26
> **NightwishFan said:**
> Why not such make an shell script to do:
```
sudo aptitude update && sudo aptitude -y safe-upgrade && sudo init 0
```

Does "init 0" need sudo?

Yes, it does. :)

---

### Post by NightwishFan on 2010-06-26
Thanks ibuclaw. I did not want to shut down to test. :)

---

### Post by matt-fender on 2010-06-26
> **tgalati4 said:**
> sudo su
apt-get update &&  apt-get -y upgrade &&  pm-suspend
apt-get install new-gf

^
pmsl

---

