---
title: "grep not working"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by grainsilo on 2010-11-01
hello I'm attempting to learn how to use the CLI with GNOME Ubuntu and am working through some tutorials but grep doesn't seem to be working. 
After typing "grep stuff" in a directory containing a file called "stuff" the cursor goes to a new blank line and just flashes until I have to end it. 
Anyone know what could be happening here? Find doesn't seem to do much either!
cheers, pete
below is what occurs

```
pete@pete-laptop:~$ cd ~
pete@pete-laptop:~$ ls
bashrc           examples.desktop  Music             podsleuth  smgTkLib
Calibre Library  firefox           nano.save         Public     stuff
Desktop          LocalApps         package_list.txt  README     Templates
Documents        mary1             Pictures          shared     Videos
Downloads        mary2.txt         Podcasts          smgLib
pete@pete-laptop:~$ grep mary1
^Z
[4]+  Stopped                 grep --color=auto mary1
pete@pete-laptop:~$ grep stuff
^Z
[5]+  Stopped                 grep --color=auto stuff
```

---

### Post by janpol on 2010-11-01
You need to run it like this:

```
ls | grep stuff
```

The | symbol is a pipeline, this way you are passing the output of the ls command, as an input to the grep command, so, grep takes that text and searches for "stuff" in it.

---

### Post by CharlesA on 2010-11-01
janpol hit it dead-on.

Also, Ctrl + Z stops a job, If you want to kill something that is actively running, you hit Ctrl + C.

---

### Post by grainsilo on 2010-11-01
cheers guys, thanks alot, not as important but why does this tutorial not say that then? [http://www.linux.org/lessons/beginner/l9/lesson9b.html](http://www.linux.org/lessons/beginner/l9/lesson9b.html)
and would anyone know of more accurate ones?
thanks again
pete

---

### Post by CharlesA on 2010-11-01
That tutorial is searching the file "Mary" for a string of text.

You are trying to search for "stuff" without telling grep where to look (which is why you get the ">" prompt).

---

### Post by cavh on 2010-11-01
You can read the documentation for grep by typing this into a terminal window:

```
man grep
```

Use the down arrow to scroll down the help file and hit the 'q' key to quit and return to the prompt.

---

