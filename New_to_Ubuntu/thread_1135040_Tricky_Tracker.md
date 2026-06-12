---
title: "Tricky Tracker"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-24
Every time i fire up, Tracker tells me 

"There was an error while performing Indexing:

Index corrupted "

-And I have to force quit to close.

Can I (you) fix this?

---

### Post by blazemore on 2009-04-24
I've had this, and solved it like this:

delete the tracker cache directory:
```
rm -rfv ~/.cache/tracker
```

go to system -> preferences -> search and index and open
click on apply and accept
if window opens saying 'do you want to index' click yes
and the message disappears

---

### Post by nnjond on 2009-04-24
Thanks. Will get bacck to you.

---

### Post by celticbhoy on 2009-04-24
If the above doesnt work have a look here - solution towards bottom of page :-

[http://ubuntuforums.org/showthread.php?t=1130773](http://ubuntuforums.org/showthread.php?t=1130773)

---

### Post by nnjond on 2009-04-24
Tracker working fine. thanks

---

### Post by blazemore on 2009-04-24
Did that help? Or did you find something else?

---

### Post by nnjond on 2009-04-24
rm -rfv ~/.cache/tracker Seems to have fixed it.

---

