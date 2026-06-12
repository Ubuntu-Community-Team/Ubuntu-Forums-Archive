---
title: "Deleting the same words in file names"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by Linux-is-super on 2011-01-19
Hi !

I have a bunch of files that begin with the same word. For instance I have about 20-30 files that in its names begins  with words:
"Linux explanation date " 
and after that word I have a different word in each file i.e. (date). It bothers me. How can I erase in each file that words before date by using terminal command ?

---

### Post by slooksterpsv on 2011-01-19
> **Linux-is-super said:**
> Hi !

I have a bunch of files that begin with the same word. For instance I have about 20-30 files that in its names begins  with words:
"Linux explanation date " 
and after that word I have a different word in each file i.e. (date). It bothers me. How can I erase in each file that words before date by using terminal command ?

Wait I'm confused, so in the file itself or in the file name?

Filename like:
linux-012345234.jpg
linux-23984.jpg
linux-28394.jpg

etc.?

or:

File1.txt:
Linux
...rest of content...

File2.txt:
Linux
...rest of content...

or what do you mean? (examples would be helpful) Technically you could write a bash script to do it for you, let me see if I can come up with it for the the filename has words you want to remove.

---

### Post by Linux-is-super on 2011-01-19
Hi slooksterpsv !

Thank you for helping.

These are the file names:
Linux explanation - date (01.05.10).wma 
Linux explanation - date (02.05.10).wma
Linux explanation - date (03.05.10).wma
.
.
.
.

and so on ..

What I want to be is:
01.05.10.wma
02.05.10.wma
03.05.10.wma
.
.
.
 and so on ...

So, new file names will be almost the same, but with erased words:
"Linux explanation - date ( " 
and also, if possible without last parentheses :
")"

---

### Post by slooksterpsv on 2011-01-19
Here it is in python:

```

import os

temp = []

for a in os.listdir("."):
        if os.path.isfile(a):
                if os.path.islink(a):
                        pass
                else:
                        temp.append(a)

for b in temp:
        c = b[b.index(".wma")-9:len(b)].replace(")","")
        os.system("mv \"" + b + "\" " + c)

```
considering it follows the naming convention specified:
alskjdfklj - aslkdjflkja (xx.xx.xx).wma

And as long as it doesn't have any " or ' in it. Just edit that in gedit, and save it in the directory you need to run it in, then run the program via, python <file_name>.py

---

### Post by Linux-is-super on 2011-01-19
Thank you slooksterpsv !

But still is there any way to use Terminal commands, like ren -rename file. I just find some link to learn Python, its new to me.

---

### Post by dracayr on 2011-01-19
[code]
for i in Linux\ explanation\ -\ date*.wma
do
mv "$i" "`echo $i|sed -e "s/.*date(\(.*\))/\1/"`"
done

---

### Post by dracayr on 2011-01-19
```

for i in Linux\ explanation\ -\ date*.wma
do
mv "$i" "`echo $i|sed -e "s/.*date(\(.*\))/\1/"`"
done

```

---

### Post by mobilediesel on 2011-01-19
The rename script works and wont overwrite files of the same name:
```
rename -v 's/^Linux explanation - date \(([0-9]{2}\.[0-9]{2}\.[0-9]{2})\)/$1/' *.wma
```
Rename is usually default on Debian-based systems.

---

### Post by mobilediesel on 2011-01-19
The rename script works and wont overwrite files of the same name:
```
rename -v 's/^Linux explanation - date \(([0-9]{2}\.[0-9]{2}\.[0-9]{2})\)/$1/' *.wma
```
Rename is usually default on Debian-based systems.

---

### Post by mobilediesel on 2011-01-19
> **Linux-is-super said:**
> Thank you slooksterpsv !

But still is there any way to use Terminal commands, like ren -rename file. I just find some link to learn Python, its new to me.

The rename script works and wont overwrite files of the same name:
```
rename -v 's/^Linux explanation - date \(([0-9]{2}\.[0-9]{2}\.[0-9]{2})\)/$1/' *.wma
```
Rename is usually default on Debian-based systems.

---

### Post by slooksterpsv on 2011-01-19
Oooo yeah mine will overwrite existing files with the same name... I didn't think about that. Umm... yeah my bash skills aren't very good at the moment. The post above seems to have given you a script that should work.

Thanks for pointing out about the overwriting existing files

---

### Post by JC Cheloven on 2011-01-19
Just in case the OP is interested: there are several GUI tools in the repos that can be used for that. For example pyrenamer.

Although I find the terminal comfortable and useful for many tasks, I like to use some gui for this one.

---

