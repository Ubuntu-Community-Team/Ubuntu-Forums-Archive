---
title: "Karmic won't restart"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-12-26
For the past week when I try to restart computer powers off but not back on. Is there a fix for this? Thanks

---

### Post by audiomick on 2009-12-26
Hallo.
I am not going to be able to solve this for you, but suggest trying
```
sudo shutdown -r now
```

This command says "shutdown as superuser and restart immediately"
For a breakdown,
```
man shutdown
```
will open the manual page for the "shutdown" command.

What this will tell you is if the "restart" button on the GUI is mixed up (computer will shut down and restart), or there is something wrong that has not to do with Ubuntu ( computer will shutdown and not restart ).

---

