---
title: "Python strangling my system"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Judgegeo on 2009-04-28
Past day or two, python seems to be going ape s***. It's sucking resources like its going out of fashion. I can usually tell because conky stops updating.

Any ideas what could be causing this? A problem with an app maybe?

Any help appreciated.

---

### Post by Anthon on 2009-04-28
Can you do
  ps -eax | fgrep python
from the commandline, that might actually get some information on which programs python is running and what is actually hogging your system.

---

