---
title: "cant open /var/log/wtmp"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-12
have tried using gedit/ and opening folder as ro0t but keep getting the red message might be binary. i am just trying to access log that shows how long and when users have been on my computer.(my daughter)

---

### Post by TeoBigusGeekus on 2010-11-12
Type 
```
last
``` 
in terminal.

---

### Post by rburkartjo on 2010-11-12
teo checked that out. how do i determine when she logged out from that command. i noticed that down means she shut  the computer down but more concerned with the time she logged out

---

### Post by TeoBigusGeekus on 2010-11-12
I think last shows the log in and out times and not the boot and shutdown ones. Someone correct me if I'm wrong.
See also
```
man last
```
for more info.

---

### Post by toekneewood on 2010-11-12
How about
```

last -Fi | head

```

---

### Post by rburkartjo on 2010-11-12
teo tks

---

