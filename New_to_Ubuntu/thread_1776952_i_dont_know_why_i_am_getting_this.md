---
title: "i dont know why i am getting this"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by raja.genupula on 2011-06-07
its asking me that "Enter password to unlock keyring"

---

### Post by raja.genupula on 2011-06-07
i really wanna make it off, how can i do that . please help me with this


thanks in advance

---

### Post by jtarin on 2011-06-07
[Here ya go!]("http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/")

---

### Post by doas777 on 2011-06-07
at some point, you asked ubuntu to remember the password to somthing (perhaps a network share?)

when ubuntu stores passwords, it encrypts them so that only the user that created them can access them. that is what the keyring password is for.

most users login manually with their password, and by default, the keyring unlocks at login, so it just uses the login password. if the user has elected to autologin however, the keyring will not be unlocked, until someone puts in the running users password.

---

### Post by raja.genupula on 2011-06-07
i did as you suggest . hope its done

---

### Post by mortez on 2012-09-11
> **jtarin said:**
> [Here ya go!]("http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/")
thanks, solved my problem!

---

