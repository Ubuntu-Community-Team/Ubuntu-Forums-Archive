---
title: "how to add desktop to the path or somewhere that let me use ALT+f2 for desktop links?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by legolas_w on 2009-11-13
Hi
I have some links on my desktop which I created them myself and I change them from time to time to reflect latest changes in installed application and so on.

To run each application I should double click on its icon in the desktop which is not good enough.

I am looking to know how I can add the desktop to the path? to let me use ALT_F2 for running links which are on my desktop.

For example: I have eclipse and eclipse2 links on my desktop. I want to use alt+f2 to run them instead of clicking on them.

Thanks

---

### Post by legolas_w on 2009-11-13
Any comment?

Thanks

---

### Post by cgb on 2009-11-13
You can edit the file ~/.bashrc and add a line as below.  Replacing <newpath> with the path to the directory you would like to add..  Will need to reboot to take effect I believe..

PATH=<newpath>:"${PATH}"

---

### Post by durand on 2009-11-13
In a terminal (Applications > Accessories > Terminal):
```
PATH=$PATH:/home/[username]/Desktop
```

You will only be able to run files that have executible permissions. Right click on the file, go to Properties > Permissions, tick Allow executing file as program.

---

### Post by durand on 2009-11-13
> **cgb said:**
> You can edit the file ~/.bashrc and add a line as below.  Replacing <newpath> with the path to the directory you would like to add..  Will need to reboot to take effect I believe..

PATH=<newpath>:"${PATH}"

You would just need to run ```
source ~/.bashrc
```

---

### Post by legolas_w on 2009-11-14
Hi

I add the relevant line to my ~/.bashrc. Now I can use terminal to launch files which are in my desktop (all of them are executable links) but I can not use ALT+F2 to lanch them.

The reason is that for example if I try to launch JDeveloper in ALT+F2 it shows something like JDeveloper.desktop  in the run menu and instead of executing the application it opens the link in the gedit.


Thanks

---

### Post by durand on 2009-11-14
Thats because you can't run .desktop files as programs. Where is the actual program located? If you open the desktop file, it should say. You can then create a shell script on your desktop to run it instead of your desktop file.

```
#!/bin/sh
/path/to/jdeveloper

```

If you then make that executable, you will be able to run it.

---

