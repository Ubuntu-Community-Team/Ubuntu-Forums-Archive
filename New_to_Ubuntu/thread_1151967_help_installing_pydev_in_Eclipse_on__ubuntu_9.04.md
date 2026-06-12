---
title: "help installing pydev in Eclipse on  ubuntu 9.04"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by pfum on 2009-05-07
hey, am trying to install Pydev 1.4.5 in Eclipse 3.2 following this 

[http://www.fabioz.com/pydev/manual_101_install.html](http://www.fabioz.com/pydev/manual_101_install.html)

and am getting this error :

PyDev Extensions (1.4.6.2760) requires plug-in "org.python.pydev (1.4.6.2760)", or compatible.

how can i install this plug-in (am new to all this :confused:)

thx.

---

### Post by Hospadar on 2009-05-07
In all honesty I don't know about pydev, but in my opinion, with a dynamic language like python, pydev gets you very little.  I prefer a good text editor, lately I've been using scribes and been pleased with the results:

[https://launchpad.net/scribes](https://launchpad.net/scribes)

There are tons of others, kate is very nice, I know a lot of people use idle for python, search around, you'll find plenty

---

### Post by kay-man on 2009-05-07
I was going to anyway, so I took the opportunity to install Pydev into Eclipse. I followed the tutorial and it installed without any problem.

The one question that comes to mind is if you're running Eclipse as root only for this install, to make sure you have all the permissions the install might need.

So i ran:

kdesudo eclipse

installed pydev, and quit eclipse.

Next I just run eclipse as myself, and I find I can create a PyDev project.

If that doesn't work you're gonna have to provide some more info as to exactly what errors you're getting

---

