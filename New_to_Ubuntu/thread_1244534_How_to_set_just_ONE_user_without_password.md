---
title: "How to set just ONE user without password"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by jacklinux on 2009-08-19
Read down for new problem!

---

### Post by LewRockwell on 2009-08-19
> **jacklinux said:**
> Hi.
How can i set a normal desktop account without a password?
Thankyou.

you'll be required to use a password initially but once signed in you can initiate the automatic login function

.

---

### Post by jacklinux on 2009-08-19
Do i do this on my account or that users account?

---

### Post by NozSpark on 2009-08-19
If you go to System, Administration, Login Window, Security

and click the "Enable Automatic login" & select the user

At sometime through this process you will have to enter the user password

---

### Post by jacklinux on 2009-08-19
Thankyou

---

### Post by Penguin Guy on 2009-08-19
It would help if you told us what you are actually trying to achieve - is this for better security, or for other computer users, or what? 

Windows admin = Linux root

Linux admins have to enter their password every time they want to do admin stuff. root does not.

---

### Post by jacklinux on 2009-08-19
its ok, it was for a friend to use my PC without having to remember a password.
im the admin

---

### Post by jacklinux on 2009-08-19
its not working. i have allowed automatic login and yet if he clicks his account...he needs a password.
what am i doing wrong?

---

### Post by jacklinux on 2009-08-19
Really need a reply soon?

---

### Post by jacklinux on 2009-08-19
Come on ubuntu, don't let me down

---

### Post by mcduck on 2009-08-19
> **jacklinux said:**
> its not working. i have allowed automatic login and yet if he clicks his account...he needs a password.
what am i doing wrong?

Does he need the password at the login screen, or after that?

If you enable automatic login, and set it to log in his user, he should never even *see* the login screen.


***
If he's asked for password *after* the login, that would be to unlock the keyring, which is unlocked automatically when normal login is used. With automatic login that's not possible so he'll either have to input the keyring password manually, or remove the keyring password completely.

In case the problem is the keyring password, here's how to change/remove it:

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "Passwords:login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by louieb on 2009-08-19
And from aysiu the creator of psychocats - [HowTo: Create a Passwordless / Guest Login (Simple Method) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=513820")

I've used it and it works.

---

