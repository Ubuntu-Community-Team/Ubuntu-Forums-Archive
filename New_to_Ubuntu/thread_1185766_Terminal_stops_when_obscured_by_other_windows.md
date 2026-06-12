---
title: "Terminal stops when obscured by other windows"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by cavemaker on 2009-06-12
When a terminal window - including the menu bar, but not the title bar - is completely cut off by other windows or the edge of the screen, it stops whatever process it is running, leaving the previously generated process text in place and the cursor blinking.  Clicking inside the terminal window restarts the process from where it left off.  

I tried arranging windows over the terminal roughly as quadrants, leaving only the opening created by their rounded corners; the terminal window counted this as not entirely obscured, and kept running its process.  Presumably this means that obscuration detection is either clever or pixel-based.  Locking the computer does cause the terminal to stop, but minimizing the terminal window and maximizing other terminal windows does not.

I am running Jaunty Jackalope.  This is not a crisis, of course, but it can be rather inconvenient at times; I would appreciate advice and insight about disabling - fixing? - this effect.  Thanks!

---

### Post by rehilliard on 2009-06-12
not sure why you're experiencing this.

i just tried a find command in a term window, and then brought the browser to focus on top of it (completely obscured)...

when i went back, the find command had completed. it had NOT when I brought the browser to focus. 

Odd.

---

### Post by LowSky on 2009-06-12
This seems like an odd issue, I have never heard of this occurring. Has this always been the case, or is it something that just started happening?

What program are you running that you need a terminal open at all times?

---

### Post by cavemaker on 2009-06-12
The computer I am using is a new school computer; the network administrator just finished installing Ubuntu on it yesterday.  I believe it was doing this when I used it yesterday, but I didn't bother to investigate and therefore cannot be sure.

[quote=LowSky]What program are you running that you need a terminal open at all times?[/quote]

The program that I'm running is a small one that I wrote in the GrISep framework, a C++ framework for high energy astronomy data analysis; it iterates through a lot of data, so the terminal needs to be up for long stretches of time.  Later stages in this project will almost certainly require me to leave the computer running overnight, and I would like to lock it - as I said, though, not a crisis.

---

