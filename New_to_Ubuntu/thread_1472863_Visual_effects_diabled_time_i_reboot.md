---
title: "Visual effects diabled time i reboot"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by m3alnemer on 2010-05-04
Hi !

My computers visual effects disable themselves every time i reboot my computer.


The easy way that i can think of right now is to create a command in the startup applications.

How do i figure out the command that does such a thing?

Please, if you can tell me how did you know it, not just what it is!:D

Thanks in advanced:D

Ubuntu Lucid 10.04 LTS

---

### Post by r-senior on 2010-05-04
Your thinking is good ;)

Same happened to me and I filed a bug. It's got some workarounds in it.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617")

Look at the linked threads for other solutions too. Many do the same thing in different ways.

---

### Post by m3alnemer on 2010-05-04
found it!

Go to system > preference > Startup Applications > Add


Name: ```
Start compiz
```
command: ```
compiz --replace
```

reboot and see it works):P!

---

