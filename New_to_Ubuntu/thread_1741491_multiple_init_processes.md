---
title: "multiple /init processes"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by pavan8085 on 2011-04-28
I am trying to debug an android phone which is booting quite slow. When we took the boot logs and generated a boot chart, we saw that there were 2 init processes!! My doubt is why is init spawning one more init? Also when I connected the phone to an ADB shell, it showed 3 init processes with ps command!! The third one being spawned by the second one!!

I read about respawing. But that happens only when a process is terminated! Here all 3 init processes are alive!

Sorry for posting this Qn in Ubuntu forums but as the Qn is related to linux in general, I am posting it here :)

---

### Post by pavan8085 on 2011-05-09
Hi All,
I found the cause for the above stated multiple /init processes problem. In Android, exec command is implemented a combination of fork()+execv(). So while running exec commands from init.rc, /init process first forks itself and then the resulting child execv()s a new binary. If this execv() fails ( which was the case with me ) and there's is no error checking, then there shall remain 2 processes with the same name ( in this case, 2 /init processes ). We added _exit() for the failed execv() case so that the failed child terminates immediately.

Cheers,
pavan

---

