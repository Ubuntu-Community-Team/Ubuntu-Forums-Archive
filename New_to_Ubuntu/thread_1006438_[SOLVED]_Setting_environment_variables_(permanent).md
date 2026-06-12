---
title: "[SOLVED] Setting environment variables (permanent)"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by bitrocker on 2008-12-09
Hello,

for some program I need to run, I need to set some environment variables. What I did was the following

```
PATH=$PATH:/some/directory/
```

and

```
A_VAR=/another/dir/
export A_VAR
```

There seems to be no need to export PATH...!?
Well, this worked fine, till I restarted. Next time in KUBUNTU A_VAR was gone, PATH set to defaults.
Don`t want to do this procedure every time I boot, so how can I make changes permanent?

---

### Post by scott_g on 2008-12-09
Not entirely sure, but you could add your code to /etc/rc.local if you want it to run each time your system starts...

```
sudo gedit /etc/rc.local
```

EDIT: other suggestions below are better...

Just a thought...
Scott

---

### Post by hyper_ch on 2008-12-09
add it to your .bashrc

```

PATH=$PATH:/some/directory/
A_VAR=/another/dir/
export A_VAR

```

upon re-login it should always be there (for that user)

---

### Post by davidbilla on 2008-12-09
You have to add that code to ~/.bashrc, if your default login shell is bash. If it is csh, then put that code in ~/.cshrc. By default, Ubuntu uses bash. You can check that by typing
```

$ echo $SHELL
```

in the terminal.

---

### Post by maandverband on 2008-12-09
> **scott_g said:**
> Not entirely sure, but you could add your code to /etc/rc.local if you want it to run each time your system starts...

```
sudo gedit /etc/rc.local
```

EDIT: other suggestions below are better...

Just a thought...
Scott

CLI-apps: use sudo:

```
sudo nano /etc/rc.local
```

Graphical apps in GNOME: use gksu:

```
gksu gedit /etc/rc.local
```

Graphical apps in KDE: use kdesu:

```
kdesu kate /etc/rc.local
```

bitrocker uses Kubuntu, so he has to use the third command.

---

