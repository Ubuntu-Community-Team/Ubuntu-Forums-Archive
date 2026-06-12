---
title: "permision problem"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by gizmo720 on 2010-10-16
i am attempting to install java on my computer (ubuntu 10.4) i downloaded the file jdk-6u22-linux-i586.bin from their site an ran in the terminal ./jdk-6u22-linux-i586.bin which returned "permision denied". I tried running the command from a shell with root permisions (launched with sudo gnome-terminal) but i still got the error.
Any ideas?

---

### Post by 3rdalbum on 2010-10-16
For a start, Java is in the Partner repository aol you don't need to manually install it (just enable the Partner repository in Software Sources and then install Java).

Secondly, Linux doesn't just let any old files run. You need to make it executable first, in the Permissions tab in properties (right click the file, go to Properties, Permissions and it's in there.). But use the repository wherever possible.

---

### Post by jtarin on 2010-10-16
Post the link you downloaded from. Sun-java is available from the repositories. [Installation notes here.]("https://help.ubuntu.com/community/Java")

---

