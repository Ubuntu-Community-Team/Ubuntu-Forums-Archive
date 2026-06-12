---
title: "How to save manual pages to disk file?"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by resander on 2011-07-05
I wanted to save the ncurses man pages (ca 1080 lines) to disk. It is quite large and it would be useful to move it to a file and use the gedit editor to find things.

So I tried Select All + Copy from the Terminal screen, but only the first page was put to the clipboard. It would be tedious to select and copy one page at a time.
Is there a more convenient way?

---

### Post by aeiah on 2011-07-05
pipe it into a text file:
```

man ncurses > ncurses.txt
```

---

### Post by resander on 2011-07-05
Many thanks.

How could I miss that?!

---

### Post by seawolf167 on 2011-07-05
Note that you can also read man pages online, just google search for "[man ncurses]("http://linux.die.net/man/3/ncurses")".

---

