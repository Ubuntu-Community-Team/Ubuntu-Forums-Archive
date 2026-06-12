---
title: "Root file system error"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by user_linux on 2011-07-22
Hi,
After I installed Wubi 10.04 and began reboot, I received the message "No root file system is defined." How can I solve this?
thx!

---

### Post by wildmanne39 on 2011-07-22
Hi, have a look at this page and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by user_linux on 2011-07-23
i went to proble #2, I copiedthe code, but my gedit file was blank, so, I couldn't save it. But a weird thing happened, earlier I received the no root file system defined message after 142% but now after 400% when ít was setting the time clock. Is this an improvement?
> **wildmanne39 said:**
> Hi, have a look at this page and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2011-07-23
Usually it's caused by an unsupported raid setup or a mix of MBR and GPT partition tables or some other partition problem that Ubuntu is sensitive to (and not windows).

Boot from a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That might show the problem.

---

