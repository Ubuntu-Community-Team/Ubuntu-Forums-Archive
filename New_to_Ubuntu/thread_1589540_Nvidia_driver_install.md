---
title: "Nvidia driver install"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by esser on 2010-10-06
Im having some driver trouble.
I get some random flickering on the screen and i have seen the same when i use windows on the computer.
So i wanna update the driver but when i try to install it through the terminal it says i cant do it because "x server" is open.
So, what do i do?
Thanks

---

### Post by marshmallow1304 on 2010-10-06
Switch to a tty2 (Ctrl+Alt+F2) and run
```
sudo service gdm stop
```

Now install the driver.

When you're finished, run
```
sudo service gdm start
```

and you'll be dumped back to the login screen.  Remember to save any documents before doing this as graphical programs will close.

---

### Post by esser on 2010-10-06
Worked like a charm.
Thank you.

---

