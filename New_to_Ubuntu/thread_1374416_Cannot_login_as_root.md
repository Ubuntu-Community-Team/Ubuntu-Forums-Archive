---
title: "Cannot login as root"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by blunderoos on 2010-01-06
I created an account for a family member as a desktop account and I logged out of my default root account and lo and behold I can't log back in to my root account as I didn't have a password configured for it and it wont let me login. Is there any way to fix this?

---

### Post by fooman on 2010-01-06
reboot and at the grub menu,  choose *recovery mode*.  if you do not see the grub menu when you boot,  press the *shift* key (*shift* for karmic,  *escape* for previous versions) during the boot to make it visible.

when the recovery mode menu appears...choose [I]Drop to root shell prompt

[/I]when you get there,  if you have forgotten your user name,  type:

```
ls /home
```and you will see a list of all the users.  next type the following:

```
passwd *username*
```where *username* is the name of the user who's password it is you want to reset (for example:  if i want to reset fooman's password,  i would type: passwd fooman).  hit enter and you will be promted for a new password....be aware that you will not see the password as you type it.  when you complete it,  press enter.  you will then be prompted to re-enter it...do so and you should be all set.

---

### Post by Iowan on 2010-01-06
Are you talking about **root**, or your default account (whatever username you chose)? Dunno if [this]("https://help.ubuntu.com/community/RootSudo") might help...

---

### Post by blunderoos on 2010-01-06
> **fooman said:**
> reboot and at the grub menu,  choose *recovery mode*.  if you do not see the grub menu when you boot,  press the *shift* key (*shift* for karmic,  *escape* for previous versions) during the boot to make it visible.

when the recovery mode menu appears...choose [I]Drop to root shell prompt

[/I]when you get there,  if you have forgotten your user name,  type:

```
ls /home
```and you will see a list of all the users.  next type the following:

```
passwd *username*
```where *username* is the name of the user who's password it is you want to reset (for example:  if i want to reset fooman's password,  i would type: passwd fooman).  hit enter and you will be promted for a new password....be aware that you will not see the password as you type it.  when you complete it,  press enter.  you will then be prompted to re-enter it...do so and you should be all set.

Somehow while pressing shift, it logged me into my account. Thanks!

---

