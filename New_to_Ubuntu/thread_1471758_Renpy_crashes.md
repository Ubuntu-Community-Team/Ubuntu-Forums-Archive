---
title: "Renpy crashes"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-05-03
I filed a bug in the last version of ubuntu and its still present in this one where renpy crashes. I have installed a newer version of renpy from source and it works fine. Why hasn't anyone updated this package, also, how do you update it?

/usr/share/games/renpy/renpy/parser.py:29: DeprecationWarning: the sets module is deprecated
  import sets
/usr/share/games/renpy/renpy/script.py:31: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted

---

### Post by nhasian on 2010-05-03
did you file the bug in launchpad?  you can also make a request there to have the latest version packaged.

---

### Post by LunaticHiatus on 2010-05-03
I filed a bug awhile ago. Its a known problem. I thought that it might be updated in lucid. I'm in the irc channel making noise. Is there anything else one can do?

---

### Post by nhasian on 2010-05-03
i suppose you can ask one of the Masters of the Universe to package it for you:

[https://launchpad.net/~motu](https://launchpad.net/~motu)

or you can package it yourself and have it uploaded to make it easier for others to install it.

---

