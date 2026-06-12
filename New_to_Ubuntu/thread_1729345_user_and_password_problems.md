---
title: "user and password problems"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by bonsaimaker on 2011-04-14
Hi if anybody can help me,I just decided to install Ubuntu 10.10 within my windows 7 and the wubi installer ask me for a user and a password ,I've tried my windows id and password,I've tried my ubuntu forums id so ,please I need to know which user and password I need to install it on my computer inside windows .:popcorn:

---

### Post by seawolf167 on 2011-04-14
If the installer needs a password to start installing - its your Windows user/password
If the login screen needs a password to start Ubuntu - its the user/password you setup during installation

---

### Post by KL_72_TR on 2011-04-14
> **seawolf167 said:**
> If the installer needs a password to start installing - its your Windows user/password
If the login screen needs a password to start Ubuntu - its the user/password you setup during installation
  	 	 	 	p { margin-bottom: 0.08in; }  Yes. I would double this.
 But you have to know that installing Ubuntu inside Windows will have performance reduce.  
 Don't be discouraged from this fact.

---

### Post by bcbc on 2011-04-14
The wubi installer asks you for an ubuntu username (whatever you want) and your password (that you must enter twice). You can choose any username (that conforms to the linux standard) and any password.

Then Wubi creates a brand new user for Ubuntu with the userid you supplied and the password. HOWEVER, when you first boot Ubuntu with Wubi, you will see your Windows user name... the reason is that Wubi uses your Windows user name as the Description of your userid.

---

