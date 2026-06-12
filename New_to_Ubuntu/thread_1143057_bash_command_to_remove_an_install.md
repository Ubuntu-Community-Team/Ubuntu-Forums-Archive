---
title: "bash command to remove an install"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by aszxcv on 2009-04-29
I am doing some programming via text editor then installing my saved files  with chmod a+x program_name .I want to remove them when I finished testing them in terminal but i dont know the bash command to do so. Havent really dugged into bash yet.

---

### Post by sisco311 on 2009-04-29
```
rm path/to/file
```

for more info read the man page of the command:
```
man rm
```
and 
[uhelp]community/UsingTheTerminal[/uhelp]

[http://linuxcommand.org/]("http://linuxcommand.org/")

---

### Post by aszxcv on 2009-04-29
here is my > rody@rody-desktop:~$ ls
Desktop                go~           HelloWorld.java~  Photos     Videos
Documents              go.py         HelloWorld.py~    Pictures   yh.sh~
Examples               go.py~        Main.java~        Public



i put ```
rm home/rody/desktop/Main.java~
```
then i get bash: home/desktop/greeting.py~: No such file or directory

---

### Post by sisco311 on 2009-04-29
```
rm /home/rody/Desktop/Main.java~
```

Linux is case sensitive. desktop is not the same as Desktop. 

if the file is in the current working directory, then simply type:
```
rm Main.java~
```
or
```
rm ./Main.java~
```

Use TAB completion: When you type paths or file names, start typing the path and hit tab. Your Terminal (shell) will complete the word for you. If nothing appears to happen, hit tab again and shell will give you all the words in that path that have the partial of what you typed.Start typing again till you are past the uniqueness of the word and hit tab to finish typing the word for you.

Please read the links from my first post.

---

### Post by kanikilu on 2009-04-29
> **aszxcv said:**
> here is my 

i put ```
rm home/rody/desktop/Main.java~
```
then i get bash: home/desktop/greeting.py~: No such file or directory

You need a forward slash in front of home (/home), or just use the shorthand (~/). For example: ```
rm ~/desktop/greeting.py~
``` *Note: "desktop" may in fact be "Desktop"...

---

### Post by aszxcv on 2009-04-29
thanks it works 

appreciate the help and links

---

