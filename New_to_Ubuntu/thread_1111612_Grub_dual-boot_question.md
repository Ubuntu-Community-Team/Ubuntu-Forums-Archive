---
title: "Grub dual-boot question"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Guy Citron on 2009-03-30
Hello all!

I am trying to dual boot XP on a slave HD and I've got it going already except for one thing - the primary Linux HD shows up as an unreadable DVD drive.

This is really more of an annoyance than anything important, but I'd like to hide the primary HD from showing up at all.

I tried to use the Hide command but it doesnt seem to work. I'm getting the idea that it only works for partitions? I want the entire HD to be undectable in XP.

Here is what my menu.lst looks like for XP loader:

title		Windows XP
map		(hd0) (hd1)
map		(hd1) (hd0)
hide		(hd0,1)
unhide		(hd1,0)
root		(hd1,0)
makeactive
chainloader	+1

Any tips appreciated!

---

### Post by 73ckn797 on 2009-03-30
Are you trying to have Ubuntu not show up in the grub boot menu when starting the computer?

---

### Post by Guy Citron on 2009-03-30
Actually, after some more investigation I figured out that this phantom DVD drive was because of Deamon Tools LOL.

Sorry, I got confused, thanks for offering the help though.

Hide/unhide works as I wanted it to.

---

