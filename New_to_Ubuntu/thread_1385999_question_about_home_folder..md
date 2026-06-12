---
title: "question about home folder."
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-01-20
Ok so I used my disk usage analyzer and it told me that my home folder or "hayden" folder was completely full like 100%. It syas it has 1.9gb inside of the home folder but its completly full. What should i do?

thanks in advance

---

### Post by Extract_Here on 2010-01-20
heres a picture

---

### Post by fromthehill on 2010-01-20
the disk usage analiser is only for analising how big each folder in your filesystem is.

if you only scan your homefolder the subfolders will make a total of 100% of your homefolder
your music makes up 37% of your entire homefolder

to see how much space is free on each partition type this in the terminal

df -h 

you probably have only one partition with ubuntu so you haven't even used 3% of your harddrive :P

---

### Post by 3rdalbum on 2010-01-20
Clear some space, start putting your files onto another disk (e.g. a removable), resize your partitions from a live CD so that your /home is bigger, or [move your home directory to another partition]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/").

EDIT: I think the previous poster is correct. What you've posted is normal, apparently your filesystem has lots of space left. But in case somebody else is looking through this thread later for suggestions, I've left my original post intact.

---

