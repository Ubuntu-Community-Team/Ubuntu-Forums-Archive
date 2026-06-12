---
title: "Screensaver"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by newport_j on 2010-09-03
When my Ubuntu 10.04 goes to screensaver, I type in my password to unlock it. It is the same password that I use to login when I start up Ubuntu. It does not accept that password. I am unsure as to why. It seems that it should use this login password.
 
When I type in su Ubuntu comes back with input password. I again type in my login password and it does not like it. I am unsure as to why. I thought the login password would apply in both of these situations.
 
If the login password does not apply, then what password does?
 
Newport_j

---

### Post by andrewthomas on 2010-09-03
> **newport_j said:**
> When my Ubuntu 10.04 goes to screensaver, I type in my password to unlock it. It is the same password that I use to login when I start up Ubuntu. It does not accept that password. I am unsure as to why. It seems that it should use this login password.
If you have changed your password, then it differs from that of your login-keyring.  You need to either change the password of your login-keyring to match that of your username or input the login-keyring password to unlock your screensaver
> **newport_j said:**
> 
When I type in su Ubuntu comes back with input password. I again type in my login password and it does not like it. I am unsure as to why. I thought the login password would apply in both of these situations.
 
If the login password does not apply, then what password does?
 
Newport_jwith su you would need to input the root password which is not set in ubuntu by default.  Use sudo instead.

---

### Post by newport_j on 2010-09-03
Okay, using JtR how do I find the pasword to unlock the screensaver? I know the login password and it does not unlock the screensaver. Also, how do I find the password using JtR for when I type su?
 
Newport_j

---

### Post by Calash on 2010-09-03
Not sure what Jtr is.

The screen saver issue seems very odd.  Have you double checked to make sure the caps lock or num lock keys are not coming on after you type your password?

As for su I think you misunderstood.  The root account is disabled in Ubuntu in favor of elevating the privilege of your user account when you need root access.  This is done via the sudo command.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by newport_j on 2010-09-07
Of course, whenenver a password that I think that I typed in correctly was rejected, the first thing that I do is check to make sure the cap lock key is not on. I am assuming that the password for the screensaver is not correct. I have to literally reset the screensaver to require no password.
 
I now need to use JtR to find what that screensaver password is. I am just curiuos now. As I said I have modified the screensaver to not require a password. Frankly, I would like to modifiy it back to requiring a password. 
 
 
Newport_j

---

### Post by TNT1 on 2010-09-07
You need to tell us what JtR is.

---

### Post by M93 on 2010-09-07
that is [John the Ripper password cracker]("http://www.openwall.com/john/")

---

### Post by M93 on 2010-09-07
[ <John the Ripper Tutorial>]("http://www.osix.net/modules/article/index.php?id=455")

---

