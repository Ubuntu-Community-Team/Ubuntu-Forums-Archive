---
title: "Is it possible to nest symbolic links?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by justinmiller87 on 2010-07-30
If I run [FONT="Courier New"]ln -s ~/shared_win_ubuntu/My\ Documents ~/Documents[/FONT], can I then run [FONT="Courier New"]ln -s /Documents/My\ Dropbox ~/Dropbox[/FONT] or should I do the full path of [FONT="Courier New"]ln -s ~/shared_win_ubuntu/My\ Documents/My\ Dropbox ~/Dropbox[/FONT]?

---

### Post by gzarkadas on 2010-07-31
Yes you can. One thing to note is that if the first link is ever deleted, then the second link will become dangling.

---

### Post by justinmiller87 on 2010-08-01
Well, now that I am back in Ubuntu, nesting didn't work at all. No problem, I just did the full link. It was honestly more of a curiosity thing than anything.

---

### Post by gzarkadas on 2010-08-02
If you did exactly the example that you posted, then it is the missing ~ in front of /Documents, in the 2nd ln command at your 1st post, that stopped you from doing it. Using a link to base another link is definitely doable; I just have confirmed it for second time.

---

