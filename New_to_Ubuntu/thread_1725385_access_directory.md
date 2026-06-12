---
title: "access directory"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by nal13 on 2011-04-09
I always hear this term and I understand the concept, but I can't figure out how to actually do it. I am trying to convert files using imagemagick, but I can't access the directory. Is there a command I'm miss? I want to go to a file that is in a folder on my desktop. 

Thank you so much and I know this is probably a stupid question.

---

### Post by TeoBigusGeekus on 2011-04-09
Your desktop folder is located in the /home folder, under a folder with your username.
So, to access it you can
```
cd /home/yourusername/Desktop
```
or
```
cd ~/Desktop
```
~: abbreviation for /home/yourusername

---

### Post by nal13 on 2011-04-09
Thank you so much. *face palm*

---

