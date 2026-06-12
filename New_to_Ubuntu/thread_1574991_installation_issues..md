---
title: "installation issues."
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Randominity on 2010-09-15
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


this is a common error i have been getting across the board. what am i doing wrong?

---

### Post by candtalan on 2010-09-15
> **Randominity said:**
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

this is a common error i have been getting across the board. what am i doing wrong?

Can you say a bit more about what you are attempting, and the circumstances?

I am not any expert, but I believe a lock is used when one item is already in use, and it prevents other changes.  A bit like preventing you sawing off a tree branch that you are at the time standing on.
A solution would be to stop the item or process which is locked first.

Are you confident that you have a good and uncorrupted initial installation of Ubuntu?

---

### Post by Randominity on 2010-09-15
i didnt sudo... apparently sudo is a magic word. that makes everything work the way it should... dont ask me why?

i still have the issue of not being able to install a 32 bit browser on a 64 bit system though... 
i need it for flash functionality..
im a total noob..

---

### Post by sikander3786 on 2010-09-15
I think you are coming from some other Linux distro and you thought you were using the root account but not the case in Ubuntu. Root is disabled by default.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Which browser are you trying to install? Firefox 64 bit is already installed in Ubuntu and you can install 32-bit flash on a 64-bit system. See here.

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

---

### Post by Rubi1200 on 2010-09-15
Also make sure you are not running things like Synaptic, Software Center, and apt-get in the terminal at the same time. 

You can have 1 instance open, but not another at the same time or it can cause errors.

---

