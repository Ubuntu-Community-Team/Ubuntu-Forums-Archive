---
title: "can't login"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by navaneethan on 2010-04-08
Here When i start my ubuntu,by entering username and password,it doesn't get into desktop.

after i entered the correct username and password login starts but after some times it gets to login prompt again doesn't enter into gnome-desktop
even i gave the "startx",but it shows

/usr/bin/startx :line157 cannot create temp file...

.......xinit:Resource temporarily unavailable(error 11)
.............
............
server error (error3)

---

### Post by Mykk on 2010-04-08
I would just try reinstalling your ubuntu desktop,

ctrl alt f2 at log in screen > sudo apt-get install ubuntu-desktop > ctrl alt f7 > restart.

(you may have to remove it first - i cant remember lol)

---

### Post by navaneethan on 2010-04-08
> **Mykk said:**
> I would just try reinstalling your ubuntu desktop,

ctrl alt f2 at log in screen > sudo apt-get install ubuntu-desktop > ctrl alt f7 > restart.

(you may have to remove it first - i cant remember lol)

when i reinstall it ....Is any data will lose or not???

---

### Post by Psumi on 2010-04-08
> **navaneethan said:**
> when i reinstall it ....Is any data will lose or not???

reinstalling packages does not remove your documents, just configurations.

And it's **sudo apt-get install --reinstall ubuntu-desktop**

If it doesn't work, go back into TTY and do **sudo dpkg-reconfigure ubuntu-desktop**

Also, when TTY asks for your password, the cursor will not move, nor give asterisks, THIS IS NORMAL, just type your password and hit enter.

---

### Post by aeiah on 2010-04-08
incidentally, startx may not work because you've already got X running (even if it isnt running properly). easiest thing to do is to do it through gdm:

```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

or simply
```

sudo /etc/init.d/gdm restart

```

---

