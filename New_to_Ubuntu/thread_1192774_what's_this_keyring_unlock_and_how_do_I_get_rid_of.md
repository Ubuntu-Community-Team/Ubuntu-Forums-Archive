---
title: "what's this keyring unlock and how do I get rid of it?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-06-20
when I lauch ubuntu I get that message. it won't let me connect to the net I have to play a game with it and connect inbetween closing the window before it pops up again then if goes away. how do I get rid of it and why did it pop up out of nowhere?

---

### Post by munky99999 on 2009-06-20
Your wifi has a wep key or wpa key which was stored on your computer. The keyring stores it and keeps it safe. Thusly you need to put in the password to get access.

---

### Post by wpshooter on 2009-06-20
> **ChubbySauce said:**
> when I lauch ubuntu I get that message. it won't let me connect to the net I have to play a game with it and connect inbetween closing the window before it pops up again then if goes away. how do I get rid of it and why did it pop up out of nowhere?

You have to make the keyring password "blank", nothing, nada.

But please don't ask me exactly how it is accomplished because every time lately that I have to install a new version of Ubuntu, I have to re-find my way to this annoying little task.  But me thinks it is hidden ever so cleverly somewhere under applications / accessories / passwords and encrypton keys.

I sure wish they would get rid of this piece of $@$((@(#$$@ !!!

---

### Post by lovinglinux on 2009-06-20
Follow this:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

