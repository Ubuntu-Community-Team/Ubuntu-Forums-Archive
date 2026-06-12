---
title: "Installed Ubuntu but Windows boots instead"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by jaimeok on 2009-07-02
Sorry I'm a newby. I installed and used Ubuntu via Wubi last night but today Windows starts by default. How can I change this? Thanx

---

### Post by camaron1 on 2009-07-02
Go to synaptic manager and install a package called STARTUPMANAGER. Go to System-administration, open the program and you'll see a menu where you can change this.

---

### Post by -kg- on 2009-07-02
From [https://wiki.ubuntu.com/WubiGuide#Wubi%20Support%20Forum]("https://wiki.ubuntu.com/WubiGuide#Wubi%20Support%20Forum"):

> How do I make Ubuntu the default boot option?

Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well.

Hope this helps.

---

