---
title: "no wired/wireless connection works on out-of-box Asus eeepc x101ch@ubuntu12.04LTS"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by bugy2 on 2014-02-05
Hello :)
I am newb with linux - i just unpacked Asus Eee PC X101CH, auto-installed Ubuntu 12.04 LTS and when i try to connect to wireless network (WPA2) it never connects + every minute or so "Disconnected" message pops-up.

When trying to connect few times message "Sorry, Ubuntu 12.04 has experienced an internal error.
```
ExecutablePath
/usr/bin/gnome-control-center
Package
gnome-control-center 1:3.4.2-0ubuntu0.2
ProblemTypeg
Crash
Title
[network]:gnome-control-center crashed with SEGV in g_cclosure_marshal_VOID_VOIDv()
ApportVersion
2.0.1-0ubuntu8
...
>SegvAnalysis
Segfault happened at: 0xae1f169; mov  0x20(%esi),%ecx
PC (0xae1f1619) ok
source "0x20(%esi)" (0x00000020) not located in a known VMA region (needed readable region)!
destination "%ecx" ok

SegvReason
reading NULL VMA
```

I would update it through cable, but cable connection seems to have the same problem.
Connecting... then disconnects. Other devices (win7/cable+winxp/wifi notebooks) work on that network.
I factory restored once already - problem persists.

---

### Post by varunendra on 2014-02-07
Hello bugy2 ! Welcome to Ubuntu Forums :)

> **bugy2 said:**
> i just unpacked Asus Eee PC X101CH, auto-installed Ubuntu 12.04 LTS
What do you mean by "auto-installed"? Do you mean "Pre-Installed? Did the notebook came with Ubuntu 12.04 already installed on it?

If so, you should report the problem to the store where you bought it from, because the problem you mentioned is not normal. Either the OS installation, or the hardware may be broken, although it may also be just some minor issue.

However, if you installed it yourself, then it is not covered by the warranty and then we may try tweaking things to make it work. But if it came with Ubuntu pre-installed, it is best to consult the store first. It is their responsibility to hand you a working system.

---

