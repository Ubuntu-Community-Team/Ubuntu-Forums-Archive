---
title: "forget root password"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-02-17
Just for informative purpose.. is there any way i can change my root password if I forget the password??

---

### Post by Joeb454 on 2011-02-17
Do you mean the password you enter when you use **sudo**?

---

### Post by kn0w-b1nary on 2011-02-17
Yes:

restart computer, and just after BIOS screen hit shift, you have to be fast, and it might take you several tries. then select recovery mode, then drop to root prompt.
type "passwd" to change root password.

Hope this helps!

---

### Post by Grenage on 2011-02-17
It's against forum policy to instruct users on enabling the root account; for their benefit.

OP:

Your own account is all you need, or any other sudo-enabled account - just enter *passwd* at a prompt.

---

### Post by kn0w-b1nary on 2011-02-17
> **Grenage said:**
> It's against forum policy to instruct users on enabling the root account; for their benefit.

I thought I was just answering his question. Sorry.

---

### Post by Grenage on 2011-02-17
> **kn0w-b1nary said:**
> I thought I was just answering his question. Sorry.

I was only mentioning it in case you didn't know. ;)

---

### Post by amitpokhrel on 2011-02-17
Thanks "grenage". I was just asking for informative purpose!!! just in case!! Not any intentions to harm anyone

---

### Post by oldos2er on 2011-02-17
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by kn0w-b1nary on 2011-02-17
> **Grenage said:**
> I was only mentioning it in case you didn't know. ;)

OK, thanks! :)

---

### Post by amitpokhrel on 2011-02-25
I think this makes ubuntu security vulnerable although helpful sometimes... is there any way to stop unauthorized users to change the pasword??

---

### Post by rburkartjo on 2011-02-25
ami there is always a back door enabling anyone to get into any system. they would have to know your user name and how to do the reset password thing to get in. what are the odds on that.

---

### Post by clhsharky on 2011-02-25
amitpokhrel

Physical access to computer leaves all OS vulnerable, unless encrypted.
Or on board chip to render computer useless.


Sharky

---

### Post by Rebelli0us on 2011-02-27
> **clhsharky said:**
> amitpokhrel

Physical access to computer leaves all OS vulnerable, unless encrypted.
Or on board chip to render computer useless.


Sharky

Correct, there is NO security, it's a myth.

---

