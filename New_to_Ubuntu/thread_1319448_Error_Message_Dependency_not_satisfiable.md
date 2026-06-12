---
title: "Error Message: Dependency not satisfiable"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by wheatpenny on 2009-11-08
When I try to install a couple of pieces of software I get the following error message:

Error: Dependency is not satisfiable: libmcrypt4.
What does this mean and what can I do about it?

---

### Post by the.phantom on 2009-11-08
hi, sorry i can't help, but i bet you are going to get asked
what software are you trying to install?
was it on the ubuntu add/remove list?
did you have all sources enabled in add remove?
gotta give details as much as you can

---

### Post by Cuddles McKitten on 2009-11-08
Another important one to add to the list: did you ever do a "partial update" or get any warnings about that?

---

### Post by Lateralis on 2009-11-08
It means that a package which is necessary for the other programme to work cannot be found in the repositories that Aptitude searches.  

A quick Google search suggests that the package libmcrypt4 can be found in the "universe" repository.  I cannot remember if this repository is used by default in Ubuntu, but I suspect it isn't.  In order to check and to add this repository, go to System -> Administration -> Software sources.  Under the Ubuntu Software tab, select the "Community maintained Open Source software (universe)" repository.  You should then be able to install the programme that you want.  =)

---

### Post by wheatpenny on 2009-11-08
[LEFT]It was gyachi and Skype that I was trying to reinstall after I reinstalled Ubuntu. But then I updated Ubuntu using the update manager and Gyachi and Skype both installed with no error messages, so apparently whatever was missing was supplied by one or more of the updates.
Thanks for the replies.
 [/LEFT]

---

