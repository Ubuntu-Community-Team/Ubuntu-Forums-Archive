---
title: "Problem during load."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by OliverChandler on 2009-05-15
Hi, complete Linux noob here. I've done my research but I cannot find a solution to my problem.

During startup, I encounter the standard loading screen and then I encounter a large script. It then begins checking hardware, the only problem being it starts checking for bluetooth; of which I do not have on my laptop.

The script is similar to:

"Checking keyboard [OK]
Checking network card [OK]
Checking bluetooth"

I should probably add that I have installed it through Wubi. Any help with this problem would be appreciated, thank you.

---

### Post by AndThenWhat on 2009-05-15
So it freezes at that step?

---

### Post by OliverChandler on 2009-05-15
It's searching for a non-existant hardware. I guess that entitles freezing?
Under normal circumstances, I could remove the option in the terminal but since I can't access the GUI, I can't do anything.

---

### Post by reg4c on 2009-05-15
But does it boot?
I do not have BT on my laptop either but it checks for it anyways, says failed and continues.

If you can boot, go to System > Prefs > Startup Apps. and disable anything that might be related to BT if it is bothering you.

---

### Post by OliverChandler on 2009-05-15
Thank you, maybe I should try some patience. 
I'll reboot in a moment, thanks for the help.

---

