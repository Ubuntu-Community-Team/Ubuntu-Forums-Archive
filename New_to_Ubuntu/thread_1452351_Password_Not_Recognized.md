---
title: "Password Not Recognized"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by mickmission on 2010-04-11
I installed Ubuntu (9.1) satisfactorily, however the next time I attempted to log on my password was not recognized. How do I change or retrieve my password.

---

### Post by Didius Falco on 2010-04-11
Here you go:

[http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

Welcome to the forums!

Regards,

Didius

---

### Post by undecim on 2010-04-11
First, make sure that you didn't just have caps lock on while typing your password the first time. (Try typing your password with caps lock on)

If that doesn't work choose "recovery mode" from the grub menu. (the menu you get when you turn on your computer. If you don't usually get a menu, hold down shift from the first screen you see when turning on your computer until you get to the menu)

Once you're at the recovery menu, choose the "root" option

type
```
passwd username
```
where username is your username. Then type in your new password. While typing that password, you won't see any characters being typed, but they are being typed, trust me. (it's a security feature so that other people can't see the length of you password)

If it says that the password was updated successfully, then type
```
reboot
```

and your new password should work.

---

