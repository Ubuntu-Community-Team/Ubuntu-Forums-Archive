---
title: "Transmission error"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Geiste on 2010-04-26
I everyone

I'm getting this error:

Transmission cannot be started
Couldn't open "/home/user/.config/transmission/lock": Input/output error

This happened after a system crash and reboot. 

I'm new in linux, so i will appreciate if you tell me how to solve this problem step by step.

Thanks

---

### Post by yetiman64 on 2010-04-26
Sounds like your system crash has left a stale lock file with transmission running at the crash.

In your home folder use CTRL + H to show hidden folders, can also be done from the view menu > view hidden files. Continue to .config/transmission folders. In transmission right click the file called lock and delete or recycle bin it (depends on how your machine is set up).

Restart tranmission, it should now work.

The lock file will be regenerated next time you use transmission. The idea of the lock file is to stop multiple instances of the same program running at the same time.

---

### Post by Geiste on 2010-04-26
yetiman64 thank you very much, it works great now

---

### Post by yetiman64 on 2010-04-26
You're welcome.:)


Edit: Could you mark your thread as solved using the thread tools drop down menu at the top of your browser window and select the "solved" option. This will help out other forum users etc., Thanks, Nev.

---

### Post by Geiste on 2010-04-26
Sure... sorry...!;-)

---

