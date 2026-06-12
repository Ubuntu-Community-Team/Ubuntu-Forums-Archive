---
title: "problem with software sources"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-03
when I tried to download and install swiftfox I got an error and also when I tried to enable medibuntu I had errors. I got the message below from trying to get swiftfox. I've done this with no problems before when I first installed Ubuntu but since I reinstalled ubuntu for the FIFTH time yesterday I'm having problems. I followed instructions from the Swiftfox web page. help as always greatly appreciated :)


E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

---

### Post by jken146 on 2010-02-03
This happens when you try to run apt more than once at a time. Perhaps you have Synaptic open and you're trying to use apt-get at the same time.

---

### Post by ajgreeny on 2010-02-03
On 9.04 and 9.10 the update manager will also open in the background if any updates are available and will show in the panel.  Shutdown this and you may be able to continue.  I have turned off this behaviour in **gconf-editor** by de-selecting the box in **apps ->update notifier ->auto launch** so now I just get the update icon as in the previous versions of ubuntu.

---

### Post by ThePinkWitch on 2010-02-03
> **ajgreeny said:**
> On 9.04 and 9.10 the update manager will also open in the background if any updates are available and will show in the panel.  Shutdown this and you may be able to continue.  I have turned off this behaviour in **gconf-editor** by de-selecting the box in **apps ->update notifier ->auto launch** so now I just get the update icon as in the previous versions of ubuntu.

Thanks, I'll try again :)

---

