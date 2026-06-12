---
title: "Still getting access denied when trying to open share"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by hitemhrd on 2009-04-08
I just upgraded to Ubuntu 8.04 and am loving it. I already shared out my printer and have been able to successfully remote control my Ubuntu desktop from my XP laptop. This is awesome.

I am now trying to share out a folder. I have shared the folder in Ubuntu and can see it from my XP machine but cannot open any files from my XP laptop. I get access denied when I try to open them. I've looked online and configured this multiple times but cannot seem to find the right answer. Any suggestions?

---

### Post by Jakey_TheSnake on 2009-04-08
I believe windows XP can't read from ext3 partitions. 

Why don't you put the folder in XP, then XP will be able to read it for sure, and Ubuntu can still add files to it.

---

### Post by matrixblue on 2009-04-08
It doesn't matter what the hosted file system is because XP doesn't have to be able to read it.

Have you tried enabling Guest Access to the folder?

---

