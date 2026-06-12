---
title: "Ubuntu logs off automatically"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by BishweshJ on 2011-07-29
I installed Ubuntu yesterday and I'm still trying to learn it. So far I've installed a few new themes and screenlets. My Ubunutu logs me off automatically and at random. I get back to the login screen and as soon as I login back its as if nothing had happened. I'm using HP Probook 4530s with core i3 sandy bridge with 4 GB RAM and intel HD 3000 graphics.

---

### Post by Redblade20XX on 2011-07-29
Check this out,

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Can you post your syslog and message log after the it logs you out?

---

### Post by CatKiller on 2011-07-30
So that you know what you're looking for, it's not logging you out. X is crashing.

---

### Post by hakermania on 2011-07-30
> **CatKiller said:**
> So that you know what you're looking for, it's not logging you out. X is crashing.
+ 1
if you run sudo kill $(pidof X) you'll be logged out!

---

### Post by BishweshJ on 2011-07-31
Well for some reason ever since I posted this, the thing hasn't crashed/logged me off. If it does it again I'll post the logs.

---

