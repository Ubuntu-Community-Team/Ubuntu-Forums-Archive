---
title: "Terminal Server Hibernate Hell!"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by tamays on 2007-03-13
I am running Ubuntu as a Terminal Server in our school, which is working fine for the most part, with one BIG exception. Every time a student is logging off and clicks on Hibernate it puts the server to sleep. Well, needless to say once the little !@#$% darlings figured out that they could shut down the network it have been hell trying to keep it up and running. Is there a way to remove or deactivate the Hibernate button? If there’s no fix for this problem, I afraid I’ll be forced to go back to a Windows network, and all of the forward thinking momentum will be lost. PLEASE HELP!!!

---

### Post by Mr. C. on 2007-03-13
[ incorrect advice given - corrected below - MrC ]

MrC

---

### Post by tamays on 2007-03-13
I have tried what you posted. Changed the appropriate line, rebooted and it did not work. Am I missing something?

---

### Post by Mr. C. on 2007-03-13
No, I gave you bad advice.  I'll correct it above, and provide it here.

This is the correct method:

From a terminal window, run gconf-editor
Go to apps/gnome-powermanager
disable "can_suspend" and/or "can_hibername" as you see fit.

Sorry for the mistake.
MrC

---

