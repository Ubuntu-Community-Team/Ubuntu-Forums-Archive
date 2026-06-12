---
title: "Evolution Email password muddle"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by John Hale on 2009-03-02
I had some loging in password issues a while back and had to drop into the repair boot section to fix them since then everytime I open evolution mail is asks for the keyring password which is my previous login password not the current one and I'd like to know who to disable this keyring password thing it's a real nuisance.

thanks

---

### Post by John Hale on 2009-03-03
bump

---

### Post by plucky on 2009-03-03
See this [thread](http://ubuntuforums.org/showthread.php?t=1081361&highlight=keyring).

Good Luck

---

### Post by gandaran on 2009-03-03
> **John Hale said:**
> I had some loging in password issues a while back and had to drop into the repair boot section to fix them since then everytime I open evolution mail is asks for the keyring password which is my previous login password not the current one and I'd like to know who to disable this keyring password thing it's a real nuisance.

thanks
easy, go to applications » passwords/keyrings » edit » preferences and remove/delete the current/default keyring profile, close, now restart evolution, when it asks to set up a keyring password don't enter any just click okay or choose the unsecured option, it won't ask you anymore for the password.

---

