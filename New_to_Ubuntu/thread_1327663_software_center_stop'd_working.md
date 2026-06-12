---
title: "software center stop'd working"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by jesseizme on 2009-11-15
i have used software center about 5 to 6 times with no problem now all the sudden when i try to install a program it stalls @ 0% and does not move

---

### Post by coldReactive on 2009-11-15
What program(s) are you trying to install?

---

### Post by jesseizme on 2009-11-15
at first i was initially trying to install open office, then i tried pidgin and then i just started trying to install random stuff but having no luck at all

---

### Post by coldReactive on 2009-11-15
> **jesseizme said:**
> at first i was initially trying to install open office, then i tried pidgin and then i just started trying to install random stuff but having no luck at all

openOffice comes installed with ubuntu by default.

Open up terminal (Applications > Accessories > Terminal) and type in

gksudo apt-get install pidgin

then hit enter. If any errors occur, give us the output.

---

### Post by jesseizme on 2009-11-15
ok i typed that in and it asked for the password, i typed in the password and it just went to a new command line like nothing happend, so i looked to see if it was installed but no luck. so i typed it again and this was the error i got .........

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to cor

---

