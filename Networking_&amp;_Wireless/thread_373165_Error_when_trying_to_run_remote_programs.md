---
title: "Error when trying to run remote programs"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by azazel00 on 2007-03-01
Hello,

On windows, using X-win32 I can log into our colleges linux server and run 'gedit' remotely and edit my files graphically, rather than using 'nano' or 'pico'.

I've tried the same on ubuntu the following way:
```

xhost xxx.xxx.xxx.xxx
ssh -l <user> xxx.xxx.xxx.xxx
export DISPLAY=my.ip.add.ress:0
firefox/xclock/gedit

```

I always get the following error message:
Gtk-WARNING **: cannot open display:

I cant find the problem.

Am I missing a command? The same thing works like a charm on Windows.
I'm open for suggestions (other than keep on doing it through windows) ;)

Regards,
az

---

### Post by Iarwain ben-adar on 2007-03-01
Hi there,

Why don't you try
```
ssh -X xxx.xxx.xxx.xxx
```

This brings up a graphical screen of what you are doing :D


Iarwain

---

### Post by azazel00 on 2007-03-01
Same error, only faster... usually it takes like a couple of second to show the error message.. with that command it throws the error instantly.

---

### Post by Iarwain ben-adar on 2007-03-01
Look for this in your /etc/ssh/sshd_config

> X11Forwarding yes

That should do the trick i think :D


Iarwain

---

### Post by azazel00 on 2007-03-01
The line is present in the /etc/ssh/sshd_config file.

Still unable to get the trick done.

---

### Post by azazel00 on 2007-03-01
Finally got it working.

Had to edit  /etc/X11/xinit/xserverrc and remove:
```
-nolisten tcp
```

Also, edit /etc/gdm/gdm.conf and set 
```
DisallowTCP=false
```

Regards,
az

---

