---
title: "Chrome Starting Automatically"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-05-05
Why is it that Google Chrome starts when the computer boots up even though it is not in the startup applications list?

---

### Post by legatek on 2010-05-05
It might be that a previous session was saved that had Chrome running at the time. Close all applications, go to System->Preferences->Startup Applications, click the tab that says Options, check the box to automatically remember running applications and log out then back in. That should reset the settings. Repeat these steps and uncheck the box.

---

### Post by EnigmaticCoder on 2010-05-05
The suggested solution didn't work, but I magically found the problem on a wild hunch.

I have another program called PenguinTV that is in the startup application list. For some reason whenever that program starts, it starts chrome too. Odd.

---

