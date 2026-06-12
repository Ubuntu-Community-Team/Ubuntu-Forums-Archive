---
title: "Compiz - How do I exclude a program from opacity settings?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by ed-koala on 2010-04-20
I like having my window transparent, but if I want to watch a video it doesn't work so well.

In my Opacity, Brightness and Saturation settings I have this for windows types - (type=Normal | Dialog | ModalDialog | Unknown)

How can I change that to exclude Movie Player only, yet let everything else be semi-transparent?  Is this even possible?

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
[http://arstechnica.com/open-source/news/2007/11/configuring-conditional-window-transparency-in-compiz.ars](http://arstechnica.com/open-source/news/2007/11/configuring-conditional-window-transparency-in-compiz.ars)

---

### Post by ed-koala on 2010-04-20
I tried those instructions. It isn't working or I'm doing something wrong.

I put title=Movie Player in the No AGRB visuals area but it still has the player transparent. What am I doing wrong?

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
title=totem

---

### Post by ed-koala on 2010-04-20
Nope, still transparent.  Perhaps another bug in Compiz under Lucid?

---

### Post by ed-koala on 2010-04-20
I found it. Under Opacity I had to add an entry specifically for Movie Player ... title=Movie Player and set the value to 100, works fine now, thanks!!!

---

### Post by winchendonsprings on 2010-05-18
also don't forget to "up" it to override any other conflicting setings. such as normal or nautilus.

took me a little to figure that out

---

