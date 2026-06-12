---
title: "Scrambled display - Ubuntu unusable - please help!"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by DylanH on 2009-05-31
(Just started using Ubuntu and Linux a week ago, so all of this is new to me.)

*Problem:*

[LIST]
[*]Ubuntu display has become a garbled mess of lines (similar - but not identical to - running a monitor at a resolution it can't support.)
[/LIST]
*Potential Causes:*

[LIST]
[*]Power outage while playing StarCraft in Wine - everything was stable before this.
[*]General graphic problems - I have an Intel 8xx graphics card which Ubuntu seems to hate. Many problems since installation including a blank screen after install that took me hours to solve. My patchwork solutions taken from various places may have contributed this problem (although Ubuntu has been running fine for days.)
[/LIST]
*Steps Already Taken:*

[LIST]
[*]Booting in recovery mode from several kernels.
[*]Uninstalling compiz.
[*]Scanning packages for errors.
[*]Scanning file system for errors.
[*]Checking screen resolution from root (1024x768)
[/LIST]

Any advice? I don't think I'll be able to solve this problem on my own!

Please let me know if you need any more information!

---

### Post by shifty_powers on 2009-05-31
my advice?

run the recovery console and use the option to fix graphical problems.

or

reinstall and use [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by DylanH on 2009-05-31
Sorry - I should have listed that I tried the graphic fix in recovery mode (no luck.)

I've also followed the steps listed in [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) - but this was several days ago (before the crash.) Strangely, it didn't have much effect - still had some graphic issues.

---

### Post by DylanH on 2009-05-31
Thanks shifty_powers! My computer is up and running again. StarCraft can now resume.

I changed a couple of things before I rebooted so I can't be sure what ultimately fixed the problem - but the most likely candidate was going through [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) for a second time (maybe I missed something when I originally went through the steps - who knows.)

For anyone who has the same problem in the future: note that you can't follow the steps listed in the guide verbatim (i.e. I don't think gedit will work from root but you can substitute in "sudo nano".)

Anyway, no reinstall needed.

Thank you again to shifty_powers (and all of the Linux pros who spend time answering questions on this forum.)

---

