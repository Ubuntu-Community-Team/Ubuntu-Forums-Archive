---
title: "Launching a program without it having internet access"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by HrKristian on 2011-09-04
As the title says, I want to launch a program, I suppose through the terminal, and block its access to the internet

is there a simple option for this, like when launching a game with -opengl?

---

### Post by Leshrac on 2011-09-04
As far as I know there is no easy way to do this, what you described would only work if the program had an option to be launched without network access (such as in the -opengl case, the option is programed into the game, not the operating system so it doesn't work with every application).
However, locking a single program out of network access does not seem like an usual thing to do, so it is unlikely that many programs have such a feature, unless it is somehow critical for the program's operation (can't think of any case, but it might exist).

You could probably use something like trickle to control the bandwidth used by individual processes and possibly even limit it to 0.

Failing that, you could use apparmor profiles, but I wouldn't call that user friendly.

---

### Post by haqking on 2011-09-04
> **HrKristian said:**
> As the title says, I want to launch a program, I suppose through the terminal, and block its access to the internet

is there a simple option for this, like when launching a game with -opengl?

have a look at apparmor

see here

[_Bodhi Zazen on Apparmor_]("http://ubuntuforums.org/showthread.php?t=1008906")

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

