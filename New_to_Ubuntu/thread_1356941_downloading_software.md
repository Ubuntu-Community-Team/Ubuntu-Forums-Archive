---
title: "downloading software"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by mikejaron on 2009-12-16
i have the newest version of ubuntu and when i download new software from ubuntu software center or packages from synaptic package manager how do i know where to find it (where is it saved to)?

---

### Post by howefield on 2009-12-16
Most packages you download will automatically install themselves and place a menu entry in the Applications menu.

There are some command line only programs that won't have a menu entry, you would use the terminal to use them.

Are you referring to specific programs here ?

---

### Post by mikejaron on 2009-12-16
yes eye candy, (gnome shell)

---

### Post by KIAaze on 2009-12-16
In case you can't find any shortcut or obvious command to start the program:
1) Get list of files:
In Synaptic: Right-click on the package -> Properties -> Installed files

CLI:
```
dpkg -L PACKAGE
```

Online:
Search for package on [http://packages.ubuntu.com/](http://packages.ubuntu.com/), click on it and then on the "list of files" for your architecture.
2) Look for files installed in "*/bin" directories. Those are most likely the executables.

---

### Post by KIAaze on 2009-12-16
> **mikejaron said:**
> yes eye candy, (gnome shell)

```
gnome-shell --replace
```
[http://live.gnome.org/GnomeShell#Running_gnome-shell_replacing_the_panel](http://live.gnome.org/GnomeShell#Running_gnome-shell_replacing_the_panel)

---

### Post by t0p on 2009-12-16
If you've installed an app and it doesn't appear in any of the Application menus, you can add it to the menu.  Right-click on the top panel where it says "Applications" and select "Edit menus".

---

### Post by mikejaron on 2009-12-16
> **KIAaze said:**
> ```
gnome-shell --replace
```
[http://live.gnome.org/GnomeShell#Running_gnome-shell_replacing_the_panel](http://live.gnome.org/GnomeShell#Running_gnome-shell_replacing_the_panel)

thanks it works great, just in case what command do i use to make it go back to normal?

---

### Post by howefield on 2009-12-16
> **mikejaron said:**
> what command do i use to make it go back to normal?

What's normal,  metacity or compiz ?

```
metacity --replace
```
```
compiz --replace
```

---

### Post by mikejaron on 2009-12-16
> **KIAaze said:**
> ```
gnome-shell --replace
```
[http://live.gnome.org/GnomeShell#Running_gnome-shell_replacing_the_panel](http://live.gnome.org/GnomeShell#Running_gnome-shell_replacing_the_panel)

so i did that and everything seems to be working fine, but now the terminal is open and not doing anything but when i try to close it, it says that "there is still a process running and closing it would stop the process" so what should i do, it seems like the "process" wont ever stop and there is nothing going on in the terminal

---

### Post by Merk42 on 2009-12-16
> **mikejaron said:**
> so i did that and everything seems to be working fine, but now the terminal is open and not doing anything but when i try to close it, it says that "there is still a process running and closing it would stop the process" so what should i do, it seems like the "process" wont ever stop and there is nothing going on in the terminal

To go back to 'normal', have the Terminal open and hit Ctrl-C

Keep in mind **GNOME Shell is still in development** as in not even beta, and you may even be better off building from source.
For more information check out the [GNOME Shell thread](http://ubuntuforums.org/showthread.php?t=1305154)

---

### Post by howefield on 2009-12-16
> **mikejaron said:**
> but now the terminal is open and not doing anything but when i try to close it, it says that "there is still a process running and closing it would stop the process"

Next time, press Alt + F2 and run the command from there, will mean you don't need to have the terminal open all the time whilst the process is running.

---

