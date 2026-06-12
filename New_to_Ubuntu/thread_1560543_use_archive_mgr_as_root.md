---
title: "use archive mgr as root?"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by stevek123 on 2010-08-25
I downloaded a file/library in zip format that I want to install to /usr/share/***. When I tried to do it from archive mgr it says I do not have permission. I googled it and found one guy who said to look in the man. Buncha gobbldygook there! How do I access root to do this ? ... OR... command line access to unzip directly to the folder?

---

### Post by jpaugh64 on 2010-08-25
All you need to know is the command-line name of the program you want to run as root: in this case, the Archive Manager.

open a terminal (Applications Menu-->Accessories-->Terminal), and type in the following after the dollar sign:
```
$ sudo file-roller
```

Then, type in your password at the prompt and open the compressed file using the Open command (Ctrl+O).

In order to actually discover the command-line name of a program to it, find a link to it in the main menu, right-click, choose "Add this launcher to Desktop", find the new link on the Desktop and right click it; then choose Properties, and look at the "Command" text box. This shows the name of the program file, which is what you need to use in the command line to run the program.

---

### Post by stevek123 on 2010-08-25
I'm sorry. I dont understand what you said. How does this extract the file into the OS portion of the program? I guess I need something more specific...   sudo archive mgr extract from... to... or something like that.

---

### Post by stevek123 on 2010-08-25
Doh! Never mind...
'sudo file-roller'   opened the GUI and it was simple from there.
Thank you.

---

### Post by wojox on 2010-08-25
Have you already unzipped it somewhere in your home directory?

---

