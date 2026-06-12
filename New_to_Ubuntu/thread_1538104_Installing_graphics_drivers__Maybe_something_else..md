---
title: "Installing graphics drivers?  Maybe something else.  Game crashes after loading."
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Zerocyber on 2010-07-24
I'm running the netbook remix 10.04 on my Lenovo S10-2 and having issues getting EverQuest working.  This is regular EQ and I know this machine can run it.  The game seems to think I have a graphics card in the NVIDIA GeForce 5 series, but it's actually the Intel GMA 950.  I spent three hours earlier Googling errors and trying various things.  Running Wine 2.0.  The game installed and patched fine.  It crashes after the login screen, when the game is actually booting up.  Which drivers do I need and how do I install them or is it something else entirely?

---

### Post by Zerocyber on 2010-07-25
Nada?

---

### Post by eyeofreason on 2010-07-25
Envy can help you to find a proper driver. It's in the repos. You might also try to install the latest Wine since the 1 in the repos is a bit old.

[http://www.winehq.org/](http://www.winehq.org/)

Good Luck!

---

### Post by Jazzy_Jeff on 2010-07-25
This is pretty much a Wine issue. You may want to post on their forums. One thing you may try. Make sure you do not have any desktop effects turned on.

---

### Post by Zerocyber on 2010-07-25
Envy?  Repos?  Already got the newest Wine.  The guys at their forum sent me here.  No desktop effects.

---

### Post by Zerocyber on 2010-07-25
Looked up Envy.  It's not supported anymore.  Jockey is the new thing, but it doesn't list anything past my wifi driver.

---

### Post by Mark Phelps on 2010-07-26
Once again, folks are giving you advice without doing any research first ...

Envy only works with Nvidia and ATI drivers, and since you have an Intel video chip, installing it would be a complete waste of time.

Also, Hardware drivers only offers Nvidia and ATI drivers, not Intel.

The Intel drivers are loaded when the system is installed, so you already have the Intel video drivers loaded.

---

