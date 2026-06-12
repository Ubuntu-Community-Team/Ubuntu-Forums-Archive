---
title: "Scripts"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-07
How does a script handle multiple lines?

For example....

Line 1 - Copy all files from folder A to folder B

Line 2 - Copy all files from folder C to folder D

Line 3 - Copy all files from Folder D back to folder A

[SIZE="2"](please don't analyze the script as that's not the point)[/SIZE]

**The Questions is........**

Will ubuntu try to execute all 3 lines at the same time or execute line 1, **[COLOR="Green"]finsh[/COLOR]** Line 1's directive(s) and THEN execute Line 2 etc or will it try to execute all 3 at the same time?  This is critical because in some cases, Line 3 is dependent on the completion of Lines 1 & 2 first.

Thx !! :P

---

### Post by CharlesA on 2010-11-07
In all the scripts I've created, it runs the next line after the first one completes.

If you want to execute them simulanously, start the command in the background by adding "&" after the command.

---

### Post by uRock on 2010-11-07
Just use the && between commands if they are on the smae line. If they are different lines, then they will finish one before moving to the next command.

---

### Post by mistypotato on 2010-11-07
Great!

I was hoping it would complete Line 1 BEFORE going to line 2 etc.

Thanks !!!  :KS:KS:KS:KS:KS

---

