---
title: "best way to display disk usage in terminal"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by muuwt1 on 2010-12-31
well ive been using 
```
du -h
``` h option for human readable

but its pretty cluttered and usually hidden files make things hard to read. i didnt see anything in the man files to exclude hideen files

also just discovered
```
 ls -s -h
```s to display size and h for human readable

what do you all use?
muuwt

---

### Post by drs305 on 2010-12-31
I wrote a guide about disk space a while back. Section 4 deals with commands to help determine disk usage and some of their advantages/limitations:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Red Raven on 2010-12-31
> **muuwt1 said:**
> well ive been using 
```
du -h
``` h option for human readable

but its pretty cluttered and usually hidden files make things hard to read. i didnt see anything in the man files to exclude hideen files

also just discovered
```
 ls -s -h
```s to display size and h for human readable

what do you all use?
muuwt


i'm new and may be way wrong, but wont gparted do it? sudo get-apt install gparted is the terminal command. to get it if you need it.

---

### Post by garvinrick4 on 2010-12-31
> **drs305 said:**
> I wrote a guide about disk space a while back. Section 4 deals with commands to help determine disk usage and some of their advantages/limitations:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) I have just noticed you have your guides in your signature was going to ask for a list to be posted.
If you have other guides would you mind posting in this thread.

---

### Post by drs305 on 2010-12-31
> **garvinrick4 said:**
> I have just noticed you
have your guides in your signature was going to ask for a list to be posted.

You can find many of my submissions by going to Search, Advanced Search and put "drs305" in the username and "Tutorials & Tips" in the search forum window. Some are a bit old but I try to keep them up-to-date. There are lots of great guides on the UF and limiting a search to a single user isn't probably the best way to find an answer....  ;-)

---

### Post by garvinrick4 on 2010-12-31
> **drs305 said:**
> You can find many of my submissions by going to Search, Advanced Search and put "drs305" in the username and "Tutorials & Tips" in the search forum window. Some are a bit old but I try to keep them up-to-date. There are lots of great guides on the UF and limiting a search to a single user isn't probably the best way to find an answer....  ;-) That was a very nice method to find the quides you have taken time to write. I really have to learn to use this forum better and all it's features.

---

### Post by muuwt1 on 2011-01-01
> **Red Raven said:**
> i'm new and may be way wrong, but wont gparted do it? sudo get-apt install gparted is the terminal command. to get it if you need it.

apt-get :p

g parted is great for big picture disk usage, but when navigating in terminal, to see how much space is being used under a certain directory, ive found du and ls to be really helpful.

i checked out the tutorial. sweet, thanks

---

