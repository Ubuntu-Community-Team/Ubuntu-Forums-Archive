---
title: "What is this?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by JaxM on 2010-06-17
I went to start my laptop earlier and I was greeted with a message at the OS start-up screen (not the login screen) that said:

>  vdevd-work [326]: open/dev/null failed: no such file or directory

I'm not sure what that means though i've been getting that a lot in the past but thought nothing of it. There was another message on the same screen that I never saw before:

> run-init: Nuking initramfs contents: Directory not empty
      [      3.372548] Kernel Panic - Not syncing: Attempted to kill init!


I really don't know what that is but I don't think it's good. Being the extremely novice Linux/computer user I wouldn't know anything about that. What just happened for me to have seen these messages? How can I fix these? Any help with this is greatly appreciated.

---

### Post by jtarin on 2010-06-17
Your first ([COLOR="DarkRed"]udevd-work[/COLOR]) seem to be a reported bug.... [Here.]("https://bugs.launchpad.net/ubuntu/+bug/575333")
[....Related to this]("https://wiki.ubuntu.com/Initramfs")
There might be quick fix,so maybe someone that is more familiar with this problem in Ubuntu can walk you through. It's not harmful,just annoying.

---

### Post by JaxM on 2010-06-18
> **jtarin said:**
> Your first ([COLOR="DarkRed"]udevd-work[/COLOR]) seem to be a reported bug.... [Here.]("https://bugs.launchpad.net/ubuntu/+bug/575333")
[....Related to this]("https://wiki.ubuntu.com/Initramfs")
There might be quick fix,so maybe someone that is more familiar with this problem in Ubuntu can walk you through. It's not harmful,just annoying.

Sweet, thanks for the info :)

---

