---
title: "How to use full disk capacity?"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by mista-ace on 2010-10-23
hey guys, the is my first time here ive read a couple of solutions here which were really helpful, but now i have this problem.
i bought a Dell latitude 2100 laptop which had Ubuntu 10.04 LTS - the Lucid Lynx about 2 months back, the hard disk capacity is 250GBs but the thing is it says that my free disk is about 42GBS and when i checked the total size of files i have its about 15Gbs .. so the total is 60Gb so i went to System>Administration>Disk Utility and this is what i found
[IMG]http://img688.imageshack.us/img688/5756/screenshot1ug.png[/IMG]

So how can i use the entire space i have? 
am waiting for your help 
thanks alot ! 
Ace

---

### Post by Perfect Storm on 2010-10-23
It already does it. It's just splitted into partitions for different stuff.

properly 
swap
/ root
/home

---

### Post by mista-ace on 2010-10-23
[COLOR=black]hey, thanks alot [[COLOR=#D40000]**Artificial Intelligence**[/COLOR]]("http://ubuntuforums.org/member.php?u=19") but i didnt understand... do you mean that i can use the space even though in the file system it says free space isnt 100+ gb?[/COLOR]

---

### Post by Perfect Storm on 2010-10-23
Well, then you have to change the size of the different partitions. Partitions is like "zones" for different things. But it can be a dangerous thing to do if you're not knowing what you're doing.

/ <root> = all the system files
/swap = place the system will use if you ran low on memory
/home = all users setting, files, etc

Try, open the terminal and use this command;
```
sudo fdisk -l
```
What does it say?

---

