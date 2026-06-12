---
title: "Problem with links on my places"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Ymurti on 2010-10-20
When I click on my places and them Home folder, gedit opens with this message:

“/home/myname is a directory. Please check that you typed the location correctly and try again”

The same thing happens if I click Places>Desktop or  Places>Documents or Places>Music.

Can someone help me to repair this problem?

---

### Post by SuaSwe on 2010-10-20
That's a pretty interesting problem right there! Is Nautilus working OK otherwise (like if you go Alt+F2 and type in 'nautilus', does it come up)? 

Maybe the problem is with some wonky media handling issue - if you can get into Nautilus, can go head to Edit > Preferences > Media and make sure that nothing there is set to open by Gedit by default?

On a related note I sense the solution may lie somewhere in gconf-editor (Alt+F2, type gconf-editor), possibly under apps > nautilus, but beats me where! Might be worth having a look though. :)

---

### Post by plucky on 2010-10-20
> **Ymurti said:**
> When I click on my places and them Home folder, gedit opens with this message:

“/home/myname is a directory. Please check that you typed the location correctly and try again”

The same thing happens if I click Places>Desktop or  Places>Documents or Places>Music.

Can someone help me to repair this problem?

Open Nautilus as above and then right click on a folder and select "Open with Other Application".

In the window that opens ,select "File Browser".


Good Luck

---

### Post by SuaSwe on 2010-10-20
plucky: Ingenius! :D I didn't think of that as I was misled by right-clicking not working on the folders under Places... Bah.

---

### Post by Ymurti on 2010-10-20
Dear SuaSwe and Plucky, 


Thank You very much the problem is solved.

:KS

Chant Hare Krishna and Be Happy!

---

