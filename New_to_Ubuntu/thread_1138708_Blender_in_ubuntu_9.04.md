---
title: "Blender in ubuntu 9.04"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Periswell on 2009-04-26
Hello

I have now updated to Ubuntu (Ubuntu-Studios) 64 bit but my favorite program does not work properly, the program being Blender. I believe that Blender needs Python 2.5 and Python 2.6 makes it not run properly. If in synaptic I remove Python 2.6 it tells me it will remove loads of programs including Blender which will wreak my system. I also have python 2.5 installed. So my question is how do I get Blender to use Python 2.5 and not 2.6? Thanks in advance.

-Joshua

---

### Post by kellemes on 2009-04-26
What version of Blender is this?
[Ubuntu Packages]("http://packages.ubuntu.com/jaunty/blender") shows a version needing Python (>= 2.6).

---

### Post by don_paolo on 2009-04-29
i did have the same problem on my old pentium 2.4. i do have a onboard graphic card. i couldn't use blender. the gui was kind of messed up. 
for now i'll go back to 8.10.
 
blender 2.48a / python 2.6 / ubuntu 9.04

---

### Post by adam77 on 2009-05-02
Hi don, I have the same problem as you. Do you think it's python related or something else???

edit:
After looking around, the GUI/display problems don't appear to be python related.

see here for example...
[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg78423.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg78423.html)

---

### Post by Proteusiq on 2009-05-06
Guys I did not fix it, BUT went other way around! I have install Blender for Windows under WINE. and it work so well with my computer!

No more white box and weird function in Blender! WORKS PERFECT for Me

Download Blender.exe one for Windows, then Install it with Wine! Then Enjoy! Till they figure out how to make it work in Ubuntu 9.04

;D

---

### Post by Jacob Christ on 2009-06-10
My gosh funny about wine, I'm having the same problems Ubuntu 9.04, Blender 2.48a and 2.49 both with same graphics problem.  Pretty unusable.

Works fine in Vista.

Jacob

---

### Post by petermax_16 on 2010-07-07
Hey Pal,

Here is the solution: [http://www.gultgu.org/node/125](http://www.gultgu.org/node/125)

---

### Post by Irvine_himself on 2010-07-27
I am using Karmic and Blender 2.53 works fine, But the linked suggestion, [in Italian I think] is good for MakeHuman 1.5 alpha.

What I did was wrote a shell  

```

#!/bin/bash
LIBGL_ALWAYS_SOFTWARE=1 makehuman

```

saved it as  "/home/me/makehuman/makehumanfix.sh"  then used right click applications/edit menus to link the shell to a launcher.

It is running from the terminal and a bit slower. but it works fine.

Ps you can have multiple installations of Python, I have 2.4, 2.5, 2.6 and 3 all installed. Given the age and  popularity  of Python, it is almost mandatory to do this. Also, all 2.xx are backward compatible, so if you try to compile a source that calls 2.4 and point it at a 2.6 installation it should work, although you will get lots of depreciation warnings.

---

