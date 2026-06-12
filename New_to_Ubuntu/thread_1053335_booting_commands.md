---
title: "booting commands"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Periswell on 2009-01-28
hello

i have a command (for the terminal) which is used to fix those annoying blue lines in mythtv but it means that i have to apply it every time i switch on, made slightly more annoying by the fact that mythtv starts up as soon as i log on so i have to exit mythtv, apply command and then open mythtv again. for some reason i cannot install gnome-session-properties which would be the graphical way to sort this problem out so i would like to know how to do this using the terminal. how do i tell ubuntu to run this command > xvattr -a XV_COLORKEY -v 66048 
everytime it boots up? thanks in advance.

-joshua

---

### Post by yoyoned on 2009-01-28
add that line to /etc/rc.local

---

### Post by Periswell on 2009-01-28
did not work

---

### Post by albinootje on 2009-01-28
> **Periswell said:**
> did not work

You can find out where the mythtv binary or shell-script lives.
Then rename it from mythtv to mythtv-real.
Then make a shell-script called mythtv where you first use the command you need (as described in your OP), and then call mythtv.real after that.

---

### Post by Periswell on 2009-01-29
ok i am compleatly confused by that, could you explain?

-joshua

---

### Post by albinootje on 2009-01-29
> **Periswell said:**
> ok i am compleatly confused by that, could you explain?

Let's assume that the application mythtv lives in /usr/bin
Then you would do this :

1) close mythtv

2)
type in :
```

sudo mv /usr/bin/mythtv /usr/bin/mythtv-real

```

3) create a new file /usr/bin/mythtv, by doing :
```

sudo gedit /usr/bin/mythtv

```
which you'll give the following content :
```

#!/bin/bash
xvattr -a XV_COLORKEY -v 66048
/usr/bin/mythtv-real

```

4) Make the new /usr/bin/mythtv executable :
```

sudo chmod +x /usr/bin/mythtv

```

5) Test it.

---

