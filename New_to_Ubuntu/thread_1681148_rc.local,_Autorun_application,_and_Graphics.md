---
title: "rc.local, Autorun application, and Graphics"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by sunruh on 2011-02-03
I have an application that works fine that uses SVGALIB for a graphics library. I am trying to run it automatically from startup by putting the path to the executable in the rc.local file. It runs the program OK if I remove any calls to my svgalib. It bunts when the vga_setmode( 640 x 480 ) function is called. (Once I log into root, this app runs fine).
 
I have not written a script, but just put the path in rc.local. Can I overcome this problem with a special script that sets up permissions?

---

### Post by sunruh on 2011-02-08
I've noticed on other programs I call from rc.local (the ones that do run) that I don't have any keyboard commands (such as getchar()) and also the printf statements do not work.  But the program runs in the background just fine, as long as it is communication with other devices or doing calculations.
 
I read somewhere else on this forum that applications called the rc.local have root privledges, so that can't be the problem.  I have a feeling that if I could figure out how to make the program display printf statements (called from rc.local), maybe that is the key to getting my svgalib functions working from rc.local.
 
Anyone?

---

### Post by Tyggna on 2011-02-08
Well, your question is probably in the wrong area.  Most people just starting with ubuntu will never bother with rc.local

I'd try reposting in Development and Programming.

It sounds like the problems you are running into are involved with your programs not having terminal access.  getchar is going to need an input stream attached to it--and rc.local will intentionally detach it from any input streams so it can run in the background.  

If you redirect the streams on it (via piping or system function calls), then you might have better success.

---

### Post by sunruh on 2011-02-10
[FONT=Times New Roman]Thanks, Tyggna.  I was brand new to the forum and didn’t realize I was in the beginner thread.  I posted a rephrased question in the general thread.[/FONT]

---

