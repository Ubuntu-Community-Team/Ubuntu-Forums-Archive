---
title: "Weird issue with Software Center"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Drizzt611 on 2010-03-23
Sorry if this is some stupid mistake I've made, but I really don't think it is.
I installed Ubuntu on my computer earlier today, and I've also got Vista on the same hard drive, with it partitioned. I'm not sure if that makes a difference, but I figure I should put that out there.

Anyway, whenever I try to download anything with Software Center, it tells me that it's waiting for other software managers to quit. While I am doing this, there are no other windows open, and the system tray is normal. I have tried messing around with settings but that hasn't really done anything.

Any advice that could help remedy this situation would be much appreciated. Thank you for your time.

---

### Post by Drizzt611 on 2010-03-23
bump.

Please help!

---

### Post by cwbar_1 on 2010-03-23
Welcome to Ubuntu!  Be patient.  In all likelyhood, your brand new system is looking for updates.  If you want to speed up the process, go to the update manager and manually check for updates.  I would suggest you install the updates first, then add all the software you would like.

---

### Post by Drizzt611 on 2010-03-23
Whoah. I went to do that, and it prompted me to install 221 updates. But when I hit install updates i got this error message

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by cwbar_1 on 2010-03-23
Follow the directions the update manager gave you.  Alt - F2 will bring up a text window.  In this window type "terminal"  (without the quotes) and then press enter.   When  the terminal opens type "sudo dpkg --configure -a"  (without the quotes)  This will repair the interrupted package management.  When it is finished, restart the system, and install the updates.

---

### Post by Drizzt611 on 2010-03-23
Thank you so much. I must admit I didn't know that Terminal was a command prompt XD
Now everything is working great!
<3 and /thread

---

