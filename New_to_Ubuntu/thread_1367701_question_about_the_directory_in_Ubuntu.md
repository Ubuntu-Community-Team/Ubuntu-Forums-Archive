---
title: "question about the directory in Ubuntu"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by thungmail on 2009-12-29
hi
I am learning Linux now. I would like to ask some questions about Unix :
1. When somebody says "Download this file and save in your home directory". What does he(she) means about the home directory. Is it /home or /home/user_name (such as home/tuan) or somewhere else 
2. After installing the new software either using command line via terminal or using Synaptic Package Manager, where the executable file of the new software ( in window, it is used to be in C:\program file\new_software\executable_file)
Thanks s lot
Tuan

---

### Post by leef on 2009-12-29
1) they mean /home/user_name
2) The binary is stored in /usr/bin unless you compiled to software yourself in which case usually /usr/local/bin

---

### Post by raymondh on 2009-12-29
For reference

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by thungmail on 2009-12-29
Thanks for all your all anwers

---

### Post by 3rdalbum on 2009-12-29
> **thungmail said:**
> 
2. After installing the new software either using command line via terminal or using Synaptic Package Manager, where the executable file of the new software ( in window, it is used to be in C:\program file\new_software\executable_file)
Thanks s lot
Tuan

You don't need to know where the program installs to. If you're meant to run it directly, then you can run it by typing its name into the terminal. If it didn't create a launcher in your menu it's probably a command-line program or a daemon that runs on startup.

If it didn't create a launcher and it IS a GUI program, then you can just right-click your Applications menu and choose Edit Menus, then add a new item. The "command" is just the name of the program.

If you want to know where the program installed to out of idle curiosity, you can find out by right-clicking the package in Synaptic, choosing Properties and then going to the Installed Files tab.

---

### Post by thungmail on 2009-12-31
Thanks for all answer.

---

