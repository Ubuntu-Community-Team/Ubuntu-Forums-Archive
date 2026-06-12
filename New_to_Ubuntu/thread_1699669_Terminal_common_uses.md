---
title: "Terminal common uses"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by steaksauce on 2011-03-04
What are the most common uses of the terminal, and why would it be choses over a GUI?

---

### Post by whatthefunk on 2011-03-04
I use a terminal for nearly everything now.  Its quicker once you get to know your way around it.  I always install with the terminal because you can see what its doing and check to make sure that everything is going alright.

---

### Post by steaksauce on 2011-03-04
> **whatthefunk said:**
> I use a terminal for nearly everything now.  Its quicker once you get to know your way around it.  I always install with the terminal because you can see what its doing and check to make sure that everything is going alright.

Quicker as in moving around the system? (like instead of accessing your home folder in "places" you just type a command that takes you to it, and if this is the case, how do you do that and why would you?)

And how do you install files via the terminal? That's something I'd like to do since I can't tell what's going on when I install files from the software center.

---

### Post by amauk on 2011-03-04
You use the terminal to run commands and/or scripts

advantages over the GUI?
it's scriptable and you can pipe the output of one program into the input of another, which is something you cannot do in the GUI

Eg.
```
find . -type f -name '*.txt' -mtime +3 -exec mv {} {}_old \;
```This finds all text files under the currect directory older than 3 days, and appends "_old" to the filename

or```
for ((i=0; i<100; i++)); do mkdir test_$i; done
```This creates 100 new directories in the current directory, named "test_0" through to "test_99"

Try doing either of those operations quickly and simply in the GUI

---

### Post by whatthefunk on 2011-03-04
I would recommend going through a bash command tutorial.  There are several of them on the web.  To answer your questions though:

```
cd directory_path
```
This will change directory

```
ls
```
This will list all the files in the directory excpet "hidden" ones

```
ls -a
```
This will list all the files including the hidden ones

```
sudo
```
This will give you temporary root access

```
sudo apt-get install name_of_program
```
This will install a program

With just a few dozen commands, you can pretty easily navigate around in a terminal.  When you get better, you can alter your .bashrc file to make shortcuts so that you can get around even faster.

---

### Post by steaksauce on 2011-03-04
Thanks, to the both of you :)
I shall look up a decent tutorial later, I'm in the midst of studying for my Network+ exam and "refinding" my Linux knowledge from the old days.

---

