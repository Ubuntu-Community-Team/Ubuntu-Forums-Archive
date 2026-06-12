---
title: "Unable to install Updates"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-31
i am using Ubuntu 8.10 from a few months.. i was able to install updates before.. but now when i try to install updates i am getting the below error:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


and even in terminal when i enter  sudo apt-get autoremove i get the following error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


i dont understand, whats wrong.. i am using a dual boot.. i have winXP as my other OS.. i installed ubuntu from XP using Wubi.. i used to go to "system>>administration>>update manager" to check and install updates..

---

### Post by taurus on 2009-01-31
Sounds like another process was running in the background while you tried to run the update manager or apt-get.

---

### Post by chethankrish on 2009-01-31
What do i do now.. do u want me to restart my computer and check if its working wright??

---

### Post by chethankrish on 2009-01-31
Thanks.. i restarted my computer.. and now every thing seems to be working just fine.. Thank you..

---

