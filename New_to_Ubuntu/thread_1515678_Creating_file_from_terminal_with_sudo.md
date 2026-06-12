---
title: "Creating file from terminal with sudo"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by brianfitz on 2010-06-22
Hi guys, hope you can help.

Trying to create a file caled 45-huawei.rules in the /etc/udev/rules.d directory and am having quite an amount of difficulty.

When I try to just create the file it says I'm not the owner. When I try to use the chown command to change the owner to myself it doesn't work, so I attempted to use the sudo command to create the file and apparently can't figure out the right syntax to do this. 

Anyone shed any light on this!? Many thanks!

Brian

---

### Post by bodhi.zazen on 2010-06-22
Graphical:

```
gksu gedit /etc/udev/rules.d/45-huawei.rules
```

Terminal:

```
sudo -e /etc/udev/rules.d/45-huawei.rules
```

---

### Post by WRDN on 2010-06-22
The terminal approach:

```
sudo touch /etc/udev/rules.d/45-huawei.rules
```

Note bodhi.zazen mentions a graphical approach above, using the gksu command. This can be entered using multiple methods, though a common way is to press Alt+F2 to open the application launcher window, then enter it there.

---

### Post by lolzwut on 2010-06-22
just login to root and try it

```
sudo su
```

```
touch 5-huawei.rules 
```

---

