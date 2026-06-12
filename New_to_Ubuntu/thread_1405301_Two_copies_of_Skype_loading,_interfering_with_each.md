---
title: "Two copies of Skype loading, interfering with each other"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-12
Some how I:

1)  Selected the "Start Skype when computer starts" in Skype (Ubuntu version of course)
2)  "Saved running apps" in Ubuntu for next start up

This was the wrong thing to do, as now I have 2 copies of Skype running and they intefere with each other's login.  How do I clean up this mess?  I only want 1 copy of Skype to start and log in when the computer starts.

Thanks in advance for any help you can provide.

---

### Post by ajgreeny on 2010-02-12
Shutdown everything that is running, including all the applications in the system tray that are started by the Startup Applications list, then tick the "Automatically remember running applications" in the Options tab of Startup Applications.  Now shutdown the system, or at least logout and login again, and hopefully only those things in your Startup Applications list will appear, nothing else.  Now repeat what you just did, but remove the tick in the "Automatically remember" box.

All should now be well again at future boots.

---

