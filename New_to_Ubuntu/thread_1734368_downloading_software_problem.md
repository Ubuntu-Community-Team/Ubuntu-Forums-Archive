---
title: "downloading software problem"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by adeee on 2011-04-20
guys i have an certain problem.
i just install ubuntu 10.04 from live cd and try to install this softwares . and softwares are not installed. and output is not good.
see screen shots.
its from [COLOR=Red]command line
[/COLOR]
[ATTACH]189548[/ATTACH]


and its from[COLOR=Red]  software center[/COLOR]

[ATTACH]189549[/ATTACH]


and its from [COLOR=Red]package manager.[/COLOR]

[ATTACH]189550[/ATTACH]

What just happened? i am confused why these softwares are not installed. i use this cd before and before its working well but now the fresh installation makes some changes.

remember i formeted previous ubuntu intallation and then install new one.
and its installed complete.

---

### Post by manishraj2011 on 2011-04-20
> **adeee said:**
> guys i have an certain problem.
i just install ubuntu 10.04 from live cd and try to install this softwares . and softwares are not installed. and output is not good.
see screen shots.
its from [COLOR=Red]command line
[/COLOR]
[ATTACH]189548[/ATTACH]


and its from[COLOR=Red]  software center[/COLOR]

[ATTACH]189549[/ATTACH]


and its from [COLOR=Red]package manager.[/COLOR]

[ATTACH]189550[/ATTACH]

What just happened? i am confused why these softwares are not installed. i use this cd before and before its working well but now the fresh installation makes some changes.

remember i formeted previous ubuntu intallation and then install new one.
and its installed complete.
As I think,  Your **package list** on the system has **not** been **refreshed**.

So, try refreshing the package list. You can do so by going to **System**-->**Administration**-->**Update manager** and click on **check for updates**. This will refresh your package list. After this you should be able to install the softwares as usual.

NOTE :- You may or may not install the updates as per your choice.That will not affect your installing any other software but having an updated system is always recommended.

---

### Post by arochester on 2011-04-20
> i use this cd before and before its working well but now the fresh installation makes some changes. ubuntu-restricted-extras is not on the CD. You need to be connected to the Internet to get it.

---

