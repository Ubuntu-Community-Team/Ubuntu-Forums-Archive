---
title: "terminal - login"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by dsmo223 on 2010-10-09
I found a shortcut on Ubuntu to get to the terminal, ctrl alt f1, but when I hit those keys it takes me to a terminal asking me to login, I type in my user name, and then I type in my password and it will not accept my password. it says login incorrect:. Can anybody help me?

---

### Post by 23dornot23d on 2010-10-09
Make sure Caps-lock is as you had it when setting the password ...

Also if you use numbers ... in the password .... check num-lock too ....

Ctrl+Alt+F7 will get you into the graphics screen ...... if you had it running before
doing Ctrl+Alt+F1

---

### Post by dsmo223 on 2010-10-10
I type the password just like I always do, caps lock off, num lock on, and even tried to just use the numbers at the top of the keyboard, and nothing works, I event went to administration -> Users and Groups to make sure that I was using the correct user name. When that didn't work, I changed my user name and I am still having the same problem. 

Thank you for any help.

---

### Post by bprins on 2010-10-10
what if you type your password as your username so that you can verify if your password really is correct? i've had some lame issues when i was really convinced caps and num lock wasn't set, while it was.

or, maybe your keyboard settings are set to a diff language? not sure if that can happen, but just try to verify if the password you type is really the correct one.

or try to log in as root? see what that does.

---

### Post by lykeion on 2010-10-10
Other than you are entering a wrong username and/or password I can't think of why logging in to virtual terminal would fail.

To get your current username you can enter this (in a normal terminal Applications menu -> Accessories -> Terminal):
```
whoami
```

---

