---
title: "Program Not Showing Up"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by candra on 2010-12-14
Greetings, 

I am using - Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010.

I recently "installed" libkexiv2-8, but it is now showing up anywhere in my computer. Normally it would come under APPLICATIONS -> OFFICE. But it is not listed there. 

Yet when I go to the Symantec Package Manager, it lists that file as being installed.

When I researched this topic in old posts, then someone gave the advice to "Try typing whereis [filename] in terminal." 

Here is what happened when i did that:

```
:~$ whereis kexi
kexi:

```

What is my next move to find this program on my computer.

Thank you, 
Candra

---

### Post by Foxheadz on 2010-12-14
Try just typing kexi into the terminal or pressing alt-f2 and typing in kexi. It might also just be a command line app.

---

### Post by 3rdalbum on 2010-12-14
"libkexiv" is only a library that provides functions for a program. You haven't actually installed the Kexi program. Hit Alt-F2 and type:

apt:kexi

to install the Kexi program.

---

### Post by candra on 2010-12-15
I have followed both of the above recommendations, but it still not showing up. 

I also followed the guidelines from this post:

[http://ubuntuforums.org/showthread.php?t=1475827](http://ubuntuforums.org/showthread.php?t=1475827)

I even tried to install the entire K-Office and that did not work. 

Once again it did not work. In all cases, the Kexi program is not showing up even though it has been installed.

Any further thoughts, suggestions? In my previous version of Ubuntu Kexi worked fine. Your further help is appreciated...

---

### Post by Elfy on 2010-12-28
Closed - duplicate - [http://ubuntuforums.org/showthread.php?t=1654341](http://ubuntuforums.org/showthread.php?t=1654341)

---

