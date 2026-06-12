---
title: "shortcut"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by dzon65 on 2009-10-30
I totally forgot how to do this.To activate 3d-flip I use the F1 key.I used to have this as a starter on my panel in 8.10.
So,I put this in the terminal:sudo apt-get install xautomation
mkdir ~/bin
gedit ~/bin/3d-flip   "enter";the gedit opens and there I put:#!/bin/sh
xte 'key F1'  "save as ..."
Back in the terminal I put this:chmod +x ~/bin/3d-flip to make it executable.
Log out and make a new starter with the command 3d-flip.
When I do this,the command isn't recognized.Must be doing something wrong.Could anyone explain to me how to do it step by step.Thanks in advance.

---

