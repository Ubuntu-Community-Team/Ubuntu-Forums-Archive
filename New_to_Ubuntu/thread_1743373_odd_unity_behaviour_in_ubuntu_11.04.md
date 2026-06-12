---
title: "odd unity behaviour in ubuntu 11.04"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by dodoss on 2011-04-29
Hi!
I have tried to install Ubuntu 11.04 from the Live CD on a desktop with windowsXP. The installation proceeds correctly, but something strange happens afterwards:
after the first reboot Ubuntu starts with Unity and running
```
/usr/lib/nux/unity_support_test -p
```
gives me all green "yes"s. Rebooting again gives me the same result: unity starts, and all green.

After the third reboot I get, on startup, the message that my system does not meet the minimum requirements for Unity and starts with the standard Gnome desktop. Another problem now arises: trying to shutdown the computer causes the OS to exit correctly but the system does not power down, and I have to manually reset to have it start again.

I'm guessing this is some sort of driver problem, because otherwise Unity wouldn't start the first two times. Any help

My system configuration:
intel d915gav motherboard
intel pentium 4 3,20GHz
ati x1550 graphics card

---

### Post by madjr on 2011-04-29
how does unity run from the live-cd environment?

---

### Post by dodoss on 2011-04-29
I have just tried it> I'm replying now from the live boot: Unity works, and the check program gives all green lights...

---

### Post by madjr on 2011-04-29
> **dodoss said:**
> I have just tried it> I'm replying now from the live boot: Unity works, and the check program gives all green lights...

try to reinstall, if that doesnt fix the issue, you might want to report it or see if someone else has the same problem with your hardware

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[http://ubuntuforums.org/showthread.php?t=734460](http://ubuntuforums.org/showthread.php?t=734460)

---

