---
title: "Firefox not closing properly"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by jhazard112 on 2011-07-20
Hi All,

I have Firefox 3.6.18 and I am having an issue with it.  Every time I close the window the process does not close.  So when I attempt to open another window later on down the road, it tells me that Firefox is already open.  So I have to go into System Monitor and KILL the process.  This is the only way that I can get it to work again.  I was wondering if this is a known issue or if there is a fix or should I put a bug report in.  Any help is much appreciated.

Hazard

---

### Post by Bodsda on 2011-07-20
I have seen this issue a few times, but never got to the bottom of the issue. I would recommend running firefox from the terminal
```

firefox

```
 
Then try and close firefox from the file menu. When you load a program from the terminal, the output from the program will be displayed on the terminal; but also, you will not get a prompt to type in more commands until the program you ran has ended. 
 
So when you close firefox, can you confirm whether the terminal returns you to a normal prompt, or if it continues to look like it is expecting output from the program?
 
Thanks,
Bodsda

---

