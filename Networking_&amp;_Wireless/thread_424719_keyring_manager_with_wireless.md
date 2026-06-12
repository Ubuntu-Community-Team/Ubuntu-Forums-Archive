---
title: "keyring manager with wireless"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by blockcipher on 2007-04-26
When my wireless connects, keymanager asks me each time to enter a password into it.  Is there a way to automate this so i dont have to do it each time?

I'm running Feisty

Thanks,

---

### Post by Liet_Kynes on 2008-02-02
Did you sort out this problem yet? I's getting mighty irritating :(

---

### Post by blockcipher on 2008-02-02
[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

---

### Post by Marlo_nl on 2008-03-09
Blockcipher,

I assume that the link you are referring to solved your problem in the end.

But can you please let us know what part of this 20-page thread did the trick for you?

By the way, are you still running Feisty or was your problem solved after upgrading to Gutsy?


Regards, Marlo

---

### Post by blockcipher on 2008-03-09
Mario,

If I recall the first post of that thread resolved my issue.  In Gutsy I had no issues with this.

---

### Post by Liet_Kynes on 2008-03-10
Upgrading to Gutsy also solved this problem for me. :)

---

### Post by Marlo_nl on 2008-03-10
Blockcipher,

Thanks a lot for your answer.

Same for me: on Gutsy I don't have issues with the keyring manager.

On an "old" Toshiba Portege 7200 Notebook, I still have to rely on Feisty. 
For some reason Ubuntu 7.10 is not fully compatible (extremely slow) on Toshiba Portege 7200 while Ubuntu 7.04 is working just fine.

I can confirm that the first post in the thread you referred to indeed solves the keyring issue on Feisty (Ubuntu 7.04). In fact I only needed to install the package libpam-keyring and add code to the file "/etc/pam.d/gdm" like described in the link below:

[http://ubuntuforums.org/showthread.php?t=407764](http://ubuntuforums.org/showthread.php?t=407764)


To summarize: the solution for the keyring issue as described in the links mentioned in this thread is relevant for Feisty (Ubuntu 7.04). 


Regards, Marlo

---

