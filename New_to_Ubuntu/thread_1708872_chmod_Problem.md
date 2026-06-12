---
title: "chmod Problem"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-03-17
Hi,

I would like to change the owner and group of being root in the "code" directory as depicted in the following output to user (shah). How should I do that. By the way, I've gone through a lot of tutorials and trials but not yet working..

```

shah@shah-laptop:~$ ls -l /home/shah
total 12068
drwxr-xr-x 18 shah shah    4096 2010-12-13 19:12 BOOK
-rwxr-xr-x  1 shah shah      53 2010-11-24 08:25 cmd_opencv
drwxr-xr-x  4 root root    4096 2011-03-06 21:29 code

```

Thanks in advance..

-alfa-

---

### Post by plucky on 2011-03-17
Try

```
sudo chown -R shah:shah code
```

in a terminal.

Good Luck

---

### Post by JKyleOKC on 2011-03-17
A simple "sudo chown -R shah:shah $HOME/code" should do it. The upper-case R tells the chown program to recurse down through all files and sub-directories. Since the current owner is root, you need the sudo to get root privilege to make the changes.

---

### Post by alfa_80 on 2011-03-17
> **plucky said:**
> Try

```
sudo chown -R shah:shah code
```in a terminal.

Good Luck


Thanks plucky that works! Just curious, what is it done by passing "shah:shah", could you clarify that?

-alfa-

---

### Post by blind2314 on 2011-03-17
chown follows this syntax
 
```
chown <flags> user:group <files/directories>
```
 
As he said, -R makes it recurse through the directories and change all the ownership(s) below. shah:shah in this case means "change the user that owns it to shah, and change the group that owns it to shah".
 
blah:jah, would change the user that owns it to blah, and the group that owns it to jah
 
EDIT:
 
So in summary, ```
 chown -R shah:shah code 
``` says recursively change the ownership of all directories and files under and including the directory code, to be owned by the user shah, and the group shah.

---

### Post by alfa_80 on 2011-03-17
> **blind2314 said:**
> chown follows this syntax
 
```
chown <flags> user:group <files/directories>
```As he said, -R makes it recurse through the directories and change all the ownership(s) below. shah:shah in this case means "change the user that owns it to shah, and change the group that owns it to shah".
 
blah:jah, would change the user that owns it to blah, and the group that owns it to jah
 
EDIT:
 
So in summary, ```
 chown -R shah:shah code 
``` says recursively change the ownership of all directories and files under and including the directory code, to be owned by the user shah, and the group shah.

What a clear explaination! Thanks blind2314 ..

---

### Post by JKyleOKC on 2011-03-17
For a not nearly so clear explanation, but one that tells you all of the options, you can type "man chown" in a terminal window. The page-up and page-down keys will scroll through the description, and the "q" key will exit the "man" program and return you to a prompt.

An even easier, but just as unclear, solution is to launch the "xman" program. I have a launcher set up in my panel, for it, so that a simple mouse click gets me the manual page for anything that I have on my system.

However, manual pages are often rather cryptic, at least until you're quite familiar with all the jargon that many of us tend to take for granted...

---

### Post by alfa_80 on 2011-03-17
> **JKyleOKC said:**
> For a not nearly so clear explanation, but one that tells you all of the options, you can type "man chown" in a terminal window. The page-up and page-down keys will scroll through the description, and the "q" key will exit the "man" program and return you to a prompt.

An even easier, but just as unclear, solution is to launch the "xman" program. I have a launcher set up in my panel, for it, so that a simple mouse click gets me the manual page for anything that I have on my system.

However, manual pages are often rather cryptic, at least until you're quite familiar with all the jargon that many of us tend to take for granted...

Thanks anyway JKyleOKC :-)

---

