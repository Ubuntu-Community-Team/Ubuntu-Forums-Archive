---
title: "Stop Apache from running on startup"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Chrissd on 2009-09-09
Hi,

As per the title really, how can I stop Apache from running on start up? I've tried checking in Preferences -> Start Up Applications, but Apache's not listed there.

Thanks in advance

---

### Post by LowSky on 2009-09-09
sudo apt-get install bum
Your Boot-Up Manager is placed into System->Administration menu

---

### Post by adam.d.clemons on 2009-09-09
If you're a bit intimidated by the terminal you could also just go to System>Preferences>Startup (or it might be under Administration) and remove the process you don't want to start from the list. You will still have to give it the administrator password to unlock the application.

---

### Post by LowSky on 2009-09-09
Apache isn't installed by default... are you trying to build a LAMP server?

---

### Post by Chrissd on 2009-10-10
> **LowSky said:**
> sudo apt-get install bum
Your Boot-Up Manager is placed into System->Administration menu

This solved it, thanks. :)

---

