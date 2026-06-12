---
title: "Warning:- Can't be authenticated"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-03-15
Just started my computer and noticed the update manager had some updates. Clicked on it as usual and a warning came up.

Said, "You are about to install software that can't be authenticated.

Packages are:-

libpurple0 (version 1:2.5.2-0ubuntu1) will be upgraded to version 1:2.5.2-0ubuntu1.1
pidgin (version 1:2.5.2-0ubuntu1) will be upgraded to version 1:2.5.2-0ubuntu1.1
pidgin-data (version 1:2.5.2-0ubuntu1) will be upgraded to version 1:2.5.2-0ubuntu1.1

So............what's occurring?

Phil

---

### Post by Elfy on 2009-03-15
At a guess you have a repo that was previously unsigned but now is - the ppa's now have signing if that is what it is

[https://help.launchpad.net/Packaging/PPA#Adding](https://help.launchpad.net/Packaging/PPA#Adding) a PPA's keys to your system

If that is not it then I would check your sources to see which it is which is not authenticating.

```
apt-cache madison pidgin
```
should tell you which source the file is coming from

---

