---
title: "Kdevelop with Cmake"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by S.G. on 2009-01-24
Does anyone know a decent tutorial to start using Kdevelop with Cmake? I can't even find the way to add paths or libraries :$

Thanks in advance,

S.

---

### Post by snova on 2009-01-24
I don't think KDevelop has a graphical build system editor for any system but Autotools. It would probably be better to learn how to manage it yourself...

Documentation should be included in **/usr/share/doc/cmake**, particularly cmake.html.

---

### Post by S.G. on 2009-01-25
Thanks, I'll have a look at that.

---

### Post by S.G. on 2009-01-25
In fact there must be some way to configure include paths with Cmake, since Kdevelop comes with some Cmake templates...

I've found, in Project Options, C++ support tab, a form to provide custom include paths. When I pass my mouse over, I get this tip: "**A semicolon-separated list of include-paths to be used while searching for headers. Paths not starting with / will be interpreted as relative to the project folder**".

I've tried to enter there my path, but it's still not working... 

Any idea about how it is done?

Thanks in advance,

S.

---

