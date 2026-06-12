---
title: "Imput/output seizure"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by nnjond on 2011-02-26
Hi,

I've installed a number of Ubuntu distros; at present I'm running 10.10. Sometimes my screen freezes and the keyboard seems to be ineffective.

ALT + SysReq + k,   Ctrl-Alt-Backspace & Ctrl-Alt-F1 all fail and sometimes 

Alt+SysRq, r, s, e, i, s, u, b won't always reboot and my next resort is to hit the warm-boot button. I understand this can damage my hardware. 

Any sugestions please


ls /proc/sys/kernel/sysrq returns an echo.

---

### Post by 3rdalbum on 2011-02-26
> **nnjond said:**
> Hi,

I've installed a number of Ubuntu distros; at present I'm running 10.10. Sometimes my screen freezes and the keyboard seems to be ineffective.

ALT + SysReq + k,   Ctrl-Alt-Backspace & Ctrl-Alt-F1 all fail and sometimes 

Alt+SysRq, r, s, e, i, s, u, b won't always reboot and my next resort is to hit the warm-boot button. I understand this can damage my hardware. 

Any sugestions please


ls /proc/sys/kernel/sysrq returns an echo.

Hitting the reset switch will not damage anything if your computer is truly frozen. If your computer is not frozen then it might cause data damage, but don't worry about pressing it as a last resort.

I would recommend you check your RAM by taking some of it out and seeing if the problem reoccurs. If it does, then put it back and take out the other RAM.

---

