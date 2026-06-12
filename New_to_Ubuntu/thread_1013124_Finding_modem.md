---
title: "Finding modem"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by joepello on 2008-12-16
OK, now I have scanModem working but,
gedit Modem/ModemData.txt 
produces a blank page.  I know there is a modem in here I am using it with XP to make this post.

---

### Post by Hospadar on 2008-12-16
That command would attempt to edit /home/<yourUserName>/Modem/Modem.txt  I suspect the file you are trying to edit is not located there.  Is there some guide you are working off of?  I would suspect the file is in /etc somewhere (but I might be totally wrong, is it some windows file?)

---

### Post by joepello on 2008-12-16
I am following the directions for identifying you modem in the help files that came with ubuntu 8.10 desktop

---

### Post by ieee488 on 2008-12-16
**scanmodem** does not produce an empty page.

You are getting a blank page because there is no such file at the path you gave to gedit to use, so it creates an empty file.

go read the instructions at
[http://linmodems.technion.ac.il/#scanModem](http://linmodems.technion.ac.il/#scanModem)
[http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

---

