---
title: "Brasero settings  question"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by SEisch on 2011-03-01
I am having a slight problem with the Brasero Disc Burner.  My problem is that I can't set the burn speed as low as I'd like to.  I wanted to burn some ISOs at 1x or 4x at the most.  The lowest speed I can select is 39x on my CD drive and 44x on my DVD drive.  With my previous operating system I used Nero and was able to select lower speeds.  Now I'm not having any luck.  I have read the user guide for Brasero, and did not find any clues there.  
Any tips, or suggestions for an alternate Disc burner would be appreciated.

---

### Post by komputes on 2011-03-01
I would open a bug against brasero. You can do this easily by running the command:
```
$ ubuntu-bug brasero
```Just to be safe include the model of your CD drive to the bug. 
This can be obtained with the command:
```
$ wodim -scanbus
```

---

