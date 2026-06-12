---
title: "Trouble running executable from command line"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by RyeGye24 on 2009-09-10
Ok, so I am pretty new to linux and very new to the linux command line and ssh. Basically, I used ssh to log in to my account at my college and wrote a quick Hello World program just to test it (which I called testing). I ran "make testing" and low and behold another file, and executable named "testing" appears in the directory. However, when i try typing "testing" into the command line and hitting enter, it just says "testing: command not found". 
Is there some sort of command for running executables that I'm not familiar with or am I missing some arguments? What am I doing wrong?

---

### Post by jondkent on 2009-09-10
try:

./testing

if that does not work, if may not be executable, so try:

chmod u+x ./testing

then try running it again:

./testing

---

