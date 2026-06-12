---
title: "How do I get the 3d mode working in Chess?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-06
Same as title, How do I get the 3d mode working in Chess?

I get some error about python?

---

### Post by noobuntu7 on 2009-03-06
Hi Gp.
You probably don't have the python libraries installed. Try opening a terminal (Applications>Accessories>Terminal) and typing:
```
sudo apt-get install python2.4 python-gtk2 python-glade2
```

If that doesn't work you can always try installing PyChess (which should work immediately). Just type:
```
sudo apt-get install pychess
```

---

### Post by muteXe on 2009-03-06
It's not worth it to be honest.  It's looks horrible.  I couldn't immediately differentiate between black and white and it was difficult to spot diagonals on which the bishops and queen could move. Stuff like that.

---

