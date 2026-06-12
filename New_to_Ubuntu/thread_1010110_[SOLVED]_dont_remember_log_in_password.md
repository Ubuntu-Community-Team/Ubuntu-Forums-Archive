---
title: "[SOLVED] dont remember log in password"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by jesse c on 2008-12-13
I dont log in to my computer but now im trying a cntl/alt/f1 path that asks for log in password and apparently its not the same password as my administrator word.How can i find out what password i used during my install?

---

### Post by Titan8990 on 2008-12-13
In order to find out the password you used to install, you would have to crack the hash. It is much easier to just reset the password.

At the grub menu (you may have to hit ESC to see it) select Ubuntu (recovery mode).

If you are using 8.04 or later, select "use root shell" when presented with the option.

To change a password:

passwd USERNAME

Then you will be prompted to enter a new password.

Then just reboot and continue as your normally would:

sudo shutdown -r now

---

### Post by bodhi.zazen on 2008-12-13
> **jesse c said:**
> I dont log in to my computer but now im trying a cntl/alt/f1 path that asks for log in password and apparently its not the same password as my administrator word.How can i find out what password i used during my install?

Unless you made some significant changes, your login password is the same as your administrative password.

So I suspect either a typo or something like caps lock being on.

Otherwise you can reset your password from the recovery mode

Drop to a command prompt and enter

```
passwd user
```

where user is the user you wish to set a password.

---

