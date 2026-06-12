---
title: "MPFR installation problem (libgmp)"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by ASEinhorn on 2011-08-05
Hi, i'm literally only a couple of days into using linux, and I have a problem I just can't seem to find the solution to.

I'm developing a game on the iphone in OSX, and it's multiplayer. In order to accomplish this i'm going to run an engine and web service on Apache. In order to install Apache however I need to install GCC, and in order to install that i discovered i need to install GMP, MPFR and MPC. I've installed GMP 5.0.2 fine (using configure/make/make check and make install). I had configuration problems with MPFR but solved them by patching it. It also makes fine, but when i do make check it gives me the error:

error while loading shared libraries: libgmp.so.10: cannot open shared object file: No such file or directory

Now, I know this exists in /usr/local/lib/ however i'm not sure whether the problem is that i need to point MPFR at this when I make, or whether this should have been installed in a more root version of /lib.

In any case even if either of these things are the problem I have no idea how to do either of these things. Any help would be very much appreciated. Thank you!

---

### Post by malele on 2012-09-22
i came across the same problem when i tried to install the mpfr(./configure-->make-->make check, then the problem came), which said:
[COLOR=Red]./tversion: error while loading shared libraries: libgmp.so.10: cannot open shared object file: No such file or directory
FAIL: tversion

[COLOR=Black]i have already installed the gmp, and can find 'libgmp.so.10' in /usr/local/lib/. Why still said 'cannot open' this file????

[/COLOR][/COLOR]

---

### Post by malele on 2012-09-22
> **malele said:**
> i came across the same problem when i tried to install the mpfr(./configure-->make-->make check, then the problem came), which said:
[COLOR=Red]./tversion: error while loading shared libraries: libgmp.so.10: cannot open shared object file: No such file or directory
FAIL: tversion

[COLOR=Black]i have already installed the gmp, and can find 'libgmp.so.10' in /usr/local/lib/. Why still said 'cannot open' this file????

[/COLOR][/COLOR]

this problem has been solved by the command:
[COLOR="Yellow"]sudo ldconfig[/COLOR]

thanks

---

