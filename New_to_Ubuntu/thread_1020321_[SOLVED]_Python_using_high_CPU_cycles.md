---
title: "[SOLVED] Python using high CPU cycles"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by chisayne on 2008-12-24
Pretty new to Linux, I'm starting to learn my way around, but this one escapes me. I opened my system monitor and was pretty shocked to see my CPU usage pegged at around 50% (would that be 100% of one of my dual cores? There's only one CPU percentage listed). The offending process was listed as Python. I pstree'd and saw Python-Python sitting on its own near the bottom, no children that I could see. I killed the python process and don't see any adverse effects... question is, is there a way to figure out what, if anything, is using it? Should it not be listed as a child in the pstree list? 

I'm running Kubuntu 8.10, using KDE/KDM for window/desktop management. I have the default widgets/panels thing active (not sure what it's called) that was loaded with kde, as well as cairo-dock.

At the time I noticed the problem I had Kate, Firefox, Thunderbird, and a Konsole terminal open, and had just launched Conky (which is where I first saw the 50% CPU). Now that I've seen it once I'll definitely do some further tests to see if not having one of these programs open prevents it from happening, but just wanted to get this post out there with the basics before I get lazy. 

Any other information that would help, let me know, and thanks for any help you all can provide.

**Edit** I restarted X, got the system back to (as close as I could recall) the state it was in at the time, and cannot for the life of me reproduce the issue. Question is then -- if something like this happens in the future, is there a way to tell, through pstree or something else, what called the process or why it started in the first place?

Thanks!

---

### Post by RealPSL on 2008-12-24
Python is generally serving up a script so if you can get to the terminal and do a ```
ps aux | grep python
``` The third column from the left is the CPU usage so you should be able to tell which one of the python scripts is causing the problem.

---

### Post by chisayne on 2008-12-25
Excellent, thanks. Like I said in the edit I couldn't get it to happen again when I tried so hopefully it was just a fluke. I'll call this solved but at least if it happens in the future I've got a better idea of what to look for.

---

### Post by iarenoob on 2010-11-10
I have a similar problem in ubuntu maverick, the offending process appears to be  /usr/share/ibus/ui/gtk/main.py

which is using 87% of my cpu

are u using ibus as well?

---

