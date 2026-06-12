---
title: "Pidgin acting unstable"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-10-26
Im having trouble with pidgin crashing, its not been a problem until now and ive not changed anything major with my system but these last few week, pidgin just stops running. Anyone had trouble with this, i think its probaly a bug, im using pidgin 2.5.5 on jaunty.

---

### Post by twright on 2009-10-26
A new version of Ubuntu is being released in 3 days including a new default instant messenger and a new version of Pidgin in the repos. Odds are that once you upgrade it should be fixed anyway.

---

### Post by Sarmacid on 2009-10-26
I've had no problems with pidgin, maybe an add on is making it crash, you should try running it without add ons and see what happens. Also run it from console so you can actually see the error output.

---

### Post by rockstarrem on 2009-10-26
Ever since I built it from source these issues have gone away. I'd try that, but first remove Pidgin. Purge it even.

---

### Post by CaptainMark on 2009-10-26
i just added the stable ppa to my repo list, seems to be okay for now, will post back if not okay. i havent added any add ons since this trouble started, also ran the debug window which closed when it crashed (when you say run console,is this the terminal?)

Ps, now ubuntu is preferring empathy over pidgin, anyone working on an empathy screenlet??

---

### Post by CaptainMark on 2009-10-28
Okay im still havin the issues, ive got the response from terminal ```
mark@mark-desktop:~$ pidgin
Segmentation fault
mark@mark-desktop:~$ 
```
Ive googled it and the main problem seems to be with proxy settings with an older version of pidgin but i dont use a proxy server and my network settings arent trying to use a proxy. Ive tried completley removing any plugins although i have no new ones installed, will see how that goes, any tips?

---

