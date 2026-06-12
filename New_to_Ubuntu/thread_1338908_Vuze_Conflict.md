---
title: "Vuze Conflict"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by planegenius on 2009-11-26
Hello,

If I type into a terminal```
sudo vuze
``` the new and updated version of vuze runs just fine.  However if I close that terminal, vuze shutsdown.  My problem is that when i go into the applications menu and try to run vuze from there, it displays the older version, but says that its updated to the latest version, even though it is displaying an older version and not the version i get from sudo vuze in the terminal. Can anyone help me to resolve this issue, it seems something is conflicting here.  I want to run the most recent version from my applications menu and stop seeing the old version.

Thanks!

---

### Post by Buuntu on 2009-11-27
```
sudo vuze &
```That command should run the program separate from the terminal so that it persists even after you close the terminal.  I realize that isn't what you asked, but I thought I would provide a temporary fix :D.

To start the correct version of your program, try editing the applications menu and re-adding the vuze entry.  Check in Applications > Edit Menu to do that.

---

### Post by stoogiebuncho on 2009-11-27
You can also use the run dialog (Alt+F2) to start programs, and then you don't have to worry about closing the terminal window later.

Also, if vuze is a graphical program (aka not command line), you should be using gksudo, as in:
```
gksudo vuze
```

---

### Post by lovinglinux on 2009-11-27
Using sudo instead of gksudo for graphical interfaces is a common mistake that could mess a lot of stuff. For example it screws Firefox ability to work properly, due to profile permissions.

Anyway, I don't think is a good idea to run vuze with sudo or gksudo, security wise. Imagine what could happen if someone gets full control of your vuze installation with root privileges. 

I think it's a good idea to purge vuze from your system, reinstall and make sure you have ownership of the configuration folder and files.

---

### Post by and.hunt on 2009-11-27
> **Buuntu said:**
> ```
sudo vuze &
```That command should run the program separate from the terminal so that it persists even after you close the terminal.  I realize that isn't what you asked, but I thought I would provide a temporary fix :D.

To start the correct version of your program, try editing the applications menu and re-adding the vuze entry.  Check in Applications > Edit Menu to do that.
That doesn't make it persist after the closing of the terminal. To keep it persistent you can start it using ```
nohup [COMMAND] &
``` which places the program in the background and sends output to a file nohup.out, or you can start the job as above with the ampersand to place the job in the background, and then disown using ```
disown [NO]
``` where [NO] is the job id, i.e. the longer number that is output on starting (if you place a job in the background you get an output line of the form [1] 8909 - where the [1] is the job number for the current terminal, the second number is what you pass to disown). However starting sudo with the ampersand is generally a bad idea, since sudo requires user input, and if you place it directly in the background you are going to have problems since you can't type in the password - i.e. the program is simply waiting for your password, but can't ask you since it's in the background.

---

