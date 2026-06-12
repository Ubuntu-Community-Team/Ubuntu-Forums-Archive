---
title: "program folder"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by pvplahing138 on 2009-11-15
hi,im new with ubuntu i have question.IN windows all download,installed programs are located in program files,but where in ubuntu? 
thanks for anwsering

---

### Post by camaron1 on 2009-11-15
> **pvplahing138 said:**
> hi,im new with ubuntu i have question.IN windows all download,installed programs are located in program files,but where in ubuntu? 
thanks for anwsering
The executables (most of) are under **file system**>**usr**>**bin**

---

### Post by nathan726 on 2009-11-15
There isn't exact equivalent of the 'Program Files'-directory in Linux. Instead of putting all files of a program into one single directory Linux puts all files of same type from all your programs in one place. So your programs are spread all around the file system, most executable files are in /usr/bin, documents in /usr/share/doc, icons in /usr/share/icons or /usr/share/pixmaps and so on. Programs may also have their own directory in /usr/share.

Short version: [Filesystem Hierarchy Standard - Wikipedia]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")
Long version: [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

Two useful terminal commands for finding out where your program are installed are 'which' and 'whereis'. 'which' will tell you where the executable file for the program is, for example 'which firefox' would respond '/usr/bin/firefox'. And 'whereis' will list you all locations where the program has it's files installed.

---

### Post by 3rdalbum on 2009-11-15
Why would you ever need to know? The package manager knows, and all executables associated with that package can be run simply by typing their name into the terminal. If you want to create a launcher, you don't need to specify the full path of the executable, just the name.

---

### Post by pvplahing138 on 2009-11-15
hi thanks guys for anwsering
i need this to because i have installed gta san andreas to ubuntu it works with wine it has some problems but hey game is running,i need to put no-cd crack into intallation folder so thats why i needed it.but its always good to know  where are your programs installed i dont know much about linux yet,but i still learn:p

---

