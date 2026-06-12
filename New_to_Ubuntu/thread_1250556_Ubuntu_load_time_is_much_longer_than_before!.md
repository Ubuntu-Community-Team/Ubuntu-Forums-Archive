---
title: "Ubuntu load time is much longer than before!"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by jbutzu on 2009-08-26
Hello.  I recently had to reinstall ubuntu (latest version) using wubi but now when ubuntu is loading i see a large string of parameters (what the computer is doing while loading) on a black screen.  A part of the dialogue says something about "swap" and this I believe may be the reason for the delay.  I don't remember this happenoing on my initial install and like I said - the load time is at least twice as long as before.  Also- it seems ubuntu is running in the very minimum - only the very basic programs seems to be installed.  Amarok, for instance was not installed and their sems to be a problem connecting to the upload database online.

Help!
John :confused:

---

### Post by NoaHall on 2009-08-26
Amarok is not installed because it's KDE. ( sudo apt-get install amarok in a terminal if you want it) The swap is a place where files are kept on your hard drive for quick access - this isn't used in Linux. The parameters is just the normal boot up. If you think there is something that shouldn't be, try disabling them from starting up when you're booting.

---

