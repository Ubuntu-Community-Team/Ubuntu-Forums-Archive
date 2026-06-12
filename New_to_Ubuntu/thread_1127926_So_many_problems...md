---
title: "So many problems.."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Axis on 2009-04-17
Ok, I put the computer into locked screen mode and left it there for about 12 hours or so. Well when I came home I moved the mouse to wake up the monitor and tried putting in my password. Well the box wasn't even there anymore to put in my password.
Tried a few things and it still wouldn't move. (including ctrl alt backspace)

Well after that I restarted the PC from the power button. When it tried to start back up it locked up 2 times right after post. Then after that I reset the CMOS. Then it ran just fine but some things failed in the start up, and it locked up again! So I restarted again and it dropped directly to maintenance mode. So I ran fsck and it fixed a few things, then I had to reboot twice from cli before I could even get to the gui. Well now that I'm logged back in metacity is the only window manager that will work and compiz wont at all. 

How can I fix all of these problems? What caused them? And how can I prevent them from happening again?

Thanks a ton for any responses!
Axis

---

### Post by por100pre1 on 2009-04-17
I think hard disk failure can be the culprit. Check the permissions of your user folder and make a backup to an external hard disk or other media.

---

### Post by Alekz_ on 2009-04-17
Well... You may want to take a look into dmesg and syslog (/var/log/syslog) and messages (/var/log/messages).

Look up for something wrong with your hardware or Operational System!

[]'s

Alekz_

---

