---
title: "HD consumption"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Shadowgamon on 2010-10-26
I started using Ubuntu about 3 weeks ago and so far ive been in love with it. I installed it on a second partion (15gb like recommended) but decided to reinstall it in a large one when I started using it more than vista. but now on the new partion (70 gb) it has started to consume a lot more memory than it did before(~20gb) I used Sbackup to move my settings and files, so there should be about the same (plus the hibernate space , which I don't use, can I get rid of it? ) is there some disk cleanup type thing or did I misjudge the size of my applications?

---

### Post by ivarn on 2010-10-26
Well, sudo apt-get clean will get rid of all memory temp.
And if you reboot, choose kernel recovery mode. in the menu you'll see "clean - try to make free space".
And on firefox you can delete the private files.
If you watched movies online you might have huge cache files in firefox's temp folder.
And you should go through your menus and see if you can remove some packages you don't need (apps and games).
Edit: install ubuntu-tweak. it has a lot of great tools for things like this (and more).

---

### Post by albert s on 2010-10-26
personally I have ubuntu ROOT on a 15G partition, then home on the rest(55G in my case), and a separate HD for other stuff now I have got it figured out,
Im still only about 8G of my home although I do keep running out of my 55G if I have been downloading or watching movies so I would say that is the problem.
even when you burn/copy/move them they are still hiding and taking up space.

---

### Post by srs5694 on 2010-10-27
There are graphical tools for analyzing filesystem use, such as baobab. (It's installed on my Ubuntu 9.10 system, and I don't recall installing it explicitly, so it's probably there by default.) These can help you track down where space is mysteriously disappearing.

---

