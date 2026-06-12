---
title: "dpkg was interrupted"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by johndingli on 2009-11-25
Hi guys i need help when updating with update manager there is an error occured dpkg was interrupted can someone please help me to solve this problem thanks

---

### Post by philinux on 2009-11-25
> **johndingli said:**
> Hi guys i need help when updating with update manager there is an error occured dpkg was interrupted can someone please help me to solve this problem thanks

It would help immensely if you posted the exact error. We not got crystal balls. :p

---

### Post by bodhi.zazen on 2009-11-25
Typically one runs ```
sudo dpkg-reconfigure -a
```The error message it self usually gives explicit directions on what command to run, you need to run the command with sudo.

---

### Post by johndingli on 2009-11-25
sorry mate here is the full error E: dpkg was interrupted you must manually run dpkg --configure -a to correct the problem

E:_cache.open()failed,please report

hope this helps thanks again

---

### Post by philinux on 2009-11-25
> **johndingli said:**
> sorry mate here is the full error E: dpkg was interrupted you must manually run dpkg --configure -a to correct the problem

E:_cache.open()failed,please report

hope this helps thanks again

As Bodhi says run that command. First open a terminal.

Apps>access>terminal

---

### Post by johndingli on 2009-11-25
thanks guys run the command as you said but the error is still there any other help pls

---

### Post by lisati on 2009-11-25
> **johndingli said:**
> thanks guys run the command as you said but the error is still there any other help pls

Any chance of copy/paste of the exact error message?

---

### Post by wojox on 2009-11-25
```

sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by johndingli on 2009-11-25
thanks my friends for the help i managed to solve the problem

---

### Post by kumar2012 on 2009-12-02
how to solve that dpkj error problem?????????????

---

### Post by bodhi.zazen on 2009-12-02
> **kumar2012 said:**
> how to solve that dpkj error problem?????????????

If you are in need of assistance, please provide more information (what are you trying to do and post the exact error message please)and unless you are having the exact same error consider starting a new thread ;)

---

