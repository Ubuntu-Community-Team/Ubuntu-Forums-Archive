---
title: "installing packages"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-31
I extract to a folder and then go to that destination..
then you open a terminal right on that screen

what command do I use to fully install the package..???.

---

### Post by halitech on 2010-03-31
what are you trying to install and where did you get it from?

---

### Post by 2hot6ft2 on 2010-03-31
> **3948ctyj said:**
> I extract to a folder and then go to that destination..
then you open a terminal right on that screen

what command do I use to fully install the package..???.
What package?
Does it have a Read Me file?
Did you read the Read Me file?

Unless you're using nautilus-open-terminal so you can right click in the folder and select Open in Terminal your terminal is actually opening in /home/yourusername/ and not in the folder you're in.
You would have to cd to that folder.

You can install nautilus-open-terminal like this to give you the right click option for any folder.
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install nautilus-open-terminal
```
You will have to enter your password which wont be displayed just type it in and hit Enter
then use
```
sudo killall nautilus
```
to restart nautilus

---

### Post by undecim on 2010-03-31
If you want to install a .deb package, then use "sudo dpkg -i package.deb"

If it's a tar.gz (i.e. source code) you will need to compile it. Take a look at the README or INSTALL files.

You will also need -dev packages of any dependencies.

---

