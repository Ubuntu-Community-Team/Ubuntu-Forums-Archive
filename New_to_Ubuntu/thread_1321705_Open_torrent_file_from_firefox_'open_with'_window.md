---
title: "Open torrent file from firefox 'open with' window"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Falc7 on 2009-11-10
When i download a torrent file, how do i set FF up so that it automatically opens it with my bit torrent client (atm deluge). Atm, if i click within firefox, open with, it takes me to a file browser, not a terminal or something, so i don't know select deluge from there

Its a small issue, but i'd like to be able to sort it out

---

### Post by coldReactive on 2009-11-10
/usr/bin

in the open with dialog, navigate to the above place (from the / filesystem) and double click deluge.

---

### Post by Falc7 on 2009-11-10
Thanks, thats it

---

### Post by coldReactive on 2009-11-10
Should be noted that this will happen with all variants sadly. Firefox needs a nice slap on the head for getting possible handlers by querying the usr/bin directory for what programs handle what files.

Like a button that says: "Automatically Determine Best Programs"

---

