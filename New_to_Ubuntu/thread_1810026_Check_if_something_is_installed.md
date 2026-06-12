---
title: "Check if something is installed"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by orrymr on 2011-07-22
Hi all
How do I check if a certain package (let's say openSSH) is installed on my machine?

Thanks

---

### Post by Volens on 2011-07-22
I'm sure there are other solutions, but here are some I would use...
 
If you can sudo:
 
```
sudo apt-get install *programname*
```
 
It will tell you if its installed or install it if it isn't 
 
Or you could try:
 
```
whereis *programname*
```
 
this will give you a directory if the program exists
 
Or you could just type in the command to start the program. If it starts you have it, if it doen't you probably don't.

---

### Post by Quackers on 2011-07-22
Open synaptic package manager and enter the name of what you are searching for in the search box. It will then appear in the main window and if it is installed it will have a green bax to its left. The box will be empty if it is not installed.

---

### Post by orrymr on 2011-07-22
Great, that works. 
And, out of interest, if I want to check from command line?

---

### Post by Azdour on 2011-07-22
Hi,

Along with Volens suggestions you could use:
```
dpkg-query -W <packagename>
```

---

