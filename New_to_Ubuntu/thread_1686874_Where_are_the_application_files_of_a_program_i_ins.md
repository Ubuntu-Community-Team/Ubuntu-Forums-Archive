---
title: "Where are the application files of a program i install"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by tweaktolive on 2011-02-13
when i install any application from synaptic , i get the icon on applications menu on desktop, but i want to know where are the files of the app stored in ?

like in windows in program files we have the app files like DLL , config files etc.

---

### Post by Adrianzr1 on 2011-02-13
depends on what you are looking for, and depends on the program

for example you can find some information of a program in the Home folder by pressing ctrl+h

some information of adobe air, twhirl, and chrome is in: /opt

---

### Post by jwcalla on 2011-02-13
In Synaptic, select the package you want information on.  Press the "Properties" button (or right click -> Properties).  Select the "Installed Files" tab.

---

### Post by Rubi1200 on 2011-02-13
> **jwcalla said:**
> In Synaptic, select the package you want information on.  Press the "Properties" button (or right click -> Properties).  Select the "Installed Files" tab.
Yep, that would be the easiest way to do it :-)

Alternatively, in the terminal:

```
locate <package_name>
```

---

### Post by gmargo on 2011-02-13
Use the **dpkg** command:
```

$ dpkg -L packagename

```

---

### Post by Nico-dk on 2011-02-13
I'm no expert (actually far from it), but I did pick up a few things regarding Linux systems in general over the past few weeks. If I provide wrong info below, I'm sure one of the experts will correct me ;)

Unlike windows, where most applications are installed into a single folder, Linux will spread installed files over several directories.

/usr/bin is commonly used for installed apps, and the apps will take "input" (eg. settings, plugins etc.) from other dirs like /usr/lib (app libraries) or /etc (configurations).
To prevent other users settings from overwriting yours, config files can also be stored in you home dir

This is a very basic explanation, but I hope you get the gist of it. More info here: [http://manpages.ubuntu.com/manpages/maverick/man7/hier.7.html](http://manpages.ubuntu.com/manpages/maverick/man7/hier.7.html)

---

