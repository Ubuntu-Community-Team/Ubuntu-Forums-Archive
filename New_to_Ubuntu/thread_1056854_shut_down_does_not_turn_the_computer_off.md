---
title: "shut down does not turn the computer off"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by meamusta on 2009-02-01
I have Ubuntu 8.10 installed with Wubi. Every time I try to shut down my laptop (LG LW20) the "shut down" just closes the operating system and leaves my laptop running. Then I need to manually press the power button for 7 seconds to turn my laptop off. Is there a solution for this?

---

### Post by fatality_uk on 2009-02-01
Could be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126140](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126140)

I know it's not a eeepc, but try this with Intel sc's

[https://help.ubuntu.com/community/EeePC/Fixes#Shutdown](https://help.ubuntu.com/community/EeePC/Fixes#Shutdown)

I don't have Ubuntu atm, but this has worked for a number of Intel based laptops I have had

---

### Post by nomemory on 2009-02-01
Try to shotdown your computer from the console (terminal):```

sudo halt
```

---

### Post by meamusta on 2009-02-01
Adding "modprobe -r snd-hda-intel" to the halt -file as advised in [https://help.ubuntu.com/community/EeePC/Fixes#Shutdown](https://help.ubuntu.com/community/EeePC/Fixes#Shutdown) works nicely. Thanks for the help :)

Shutting down from the terminal made no difference before I modified the halt -file.

---

