---
title: "system log disappeared"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by minsf on 2009-03-11
_Problem:_ all system logs (auth.log, kern.log, syslog, etc...) disappeared from the gnome menu (System>Administration>SystemLogs), except Xorg.0.log. i can still see them from the command line, say with "less /var/log/syslog" but how do i get them back to the SystemLog application?

_some more details:_ I accidentally ran "sudo usermod -G floppy" which removed all my groups. This probably removed my permissions to view the logs. Then I recovered the groups using a recovery boot into root shell, but the logs are still missing from the SystemLog application. The groups recovered: admin, adm, dialout, cdrom, floppy, video, plugdev, lpadmin, sambashare. (and of course the "minsf" group) did I forget some group?

let me know if you need more info

---

### Post by ibuclaw on 2009-03-11
Nope, the groups are fine (you have more than me :))

To add the log files back, go into **System->Administration->System Log**

And click **File->Open** in application tab menu.

Then add the log files you want back.

Regards
Iain

---

### Post by minsf on 2009-03-11
many thanks!
the solution is so simple that it makes me blush... i guess i was looking into groups too much, rather than thinking...
one more question while we are at it: is there a way to add logs that require root permissions to te SystemLog application? i guess the simplicity of the solution made me hungry :) so i added many logs, but i cannot add logs that require sudo, such as rkhunter's logs.

---

