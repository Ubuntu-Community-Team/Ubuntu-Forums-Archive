---
title: "problems after upgrade"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by kaushik_roy on 2011-01-01
i recently upgraded from 10.04 to 10.10. After that i accidentally did something with my graphics. now when i try logging in, i come back to the log in screen again. I can however login in safe desktop mode. In the safe mode when i click the 3d settings(under system- administration-3d). the system restarts and i find myself at the login screen again. i think there is some problems with the graphic settings. i have a lenovo AEQ laptop with  intel gma 4500 graphic. please help me correct the problem.

---

### Post by mastablasta on 2011-01-01
have you tried to go to system->administration->hardware drivers and see if you can enable drivers there? 

Also if you had any proprietary intel drivers installed before you should have removed them prior to upgrade.

---

### Post by kaushik_roy on 2011-01-01
hi thanks for helping. i was actually fiddling with my display settings when the problem occurred. This is what solved the problem:
1.i removed xserver completely by the command 
"sudo apt-get remove -- purge xserver-xorg"
the installed it again
"sudo apt-get install xserver-xorg"
then restarted the computer and bingo i could log in normally again.

---

