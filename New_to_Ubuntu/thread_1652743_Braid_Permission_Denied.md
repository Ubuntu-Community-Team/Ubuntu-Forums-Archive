---
title: "Braid Permission Denied"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by holy.zarquon on 2010-12-25
Hey guys,

Just bought the Humble Indie Bundle #2.  I installed Braid on Ubuntu 10.04 (64bit).  An error message popped up in the terminal when I ran the .bin but the installer popped up anyway.  I've since completely forgotten what that error message said. Anyway, everything seems to have installed fine but nothing happens when click on Braid in Applications > Games.  I ran it through terminal and it gave me this error.

```
bash: /home/holyzarquon/.local/share/applications/number-none_com-braid_1.desktop: Permission denied
```

Any thoughts?

---

### Post by Verbeck on 2010-12-25
from a terminal, try
*sudo chmod 777 /home/holyzarquon/.local/share/applications/number-none_com-braid_1.desktop*

---

### Post by themusicalduck on 2010-12-25
Did you install it as root? If holy.zarquon's suggestion doesn't work then it might be worth trying to install it as a normal user.

Although might be a good idea to run the braid uninstaller as root first before re-installing if you can find it.

---

### Post by 3rdalbum on 2010-12-25
You can't run a .desktop file, it is just a launcher.

Open that file in a text editor and you will see the command that it points to.

---

### Post by holy.zarquon on 2010-12-30
Verbeck: Alright, I tried the code and it asked me for my password, which I entered, and then nothing happened.

themusicalduck: I don't know what this means.. sorry

3rdalbum: I tried opening the file with gedit, it said it couldn't do it.

---

### Post by holy.zarquon on 2010-12-31
Hey guys, thanks for all your attempts to help me.  Turned out to be an openGL problem, i was just going about the trouble-shooting the wrong way.  My brother (who's had a couple cups of ubuntu) helped me out.

---

### Post by RastaCalavera on 2011-02-28
what did you do for open GL? I am having similar issues

---

### Post by holy.zarquon on 2011-02-28
I believe he fixed it by running it in windowed mode.

---

