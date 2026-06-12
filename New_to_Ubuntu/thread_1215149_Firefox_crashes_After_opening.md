---
title: "Firefox crashes After opening"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by linux_nood on 2009-07-16
well u guys i really like the ubuntu 9.04 jaunty. but now i have this problem when i open firefox it would take to long time to open and after is open i go to any web site and it would turn into a gray screen and then just close by it self....so after that i would go to the terminal and type firefox and a BUS ERROR message comes up could any one help me in this little problem

---

### Post by mano cazalet on 2009-07-16
first i would try to back up bookmarks

and then remove ~/.mozilla/firefox/ directory
to see if works

---

### Post by Tman5293 on 2009-07-16
Back up your bookmarks then use package manager to remove firefox then reinstall it

---

### Post by linux_nood on 2009-07-17
i try removing firefox but it just dont work......
and now it just dont open any more

---

### Post by lovinglinux on 2009-07-17
Run this command in terminal:

```
killall firefox
firefox -P
```

This will launch the profile manager. If it opens, create a new profile and start it.

Post any errors displayed in the terminal.

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by lovinglinux on 2009-07-17
If the profile manager doesn't start after doing the suggestions above, then try this:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Then start firefox again.

---

