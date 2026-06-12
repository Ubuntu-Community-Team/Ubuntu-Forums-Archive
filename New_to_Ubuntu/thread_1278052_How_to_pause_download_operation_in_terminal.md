---
title: "How to pause download operation in terminal"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-09-29
Is there a way to pause the upgrade or package installation in terminal

---

### Post by pmlxuser on 2009-09-29
ctrl + c (cancels it but next time start from where you left)

ctrl + z (stops process but then you can't do another process as it remains locked to the first one)

---

### Post by humphreybc on 2009-09-29
Generally just closing the terminal while it's downloading will pause it, and it'll start downloading from where it left off next time.

Closing the terminal while it's INSTALLING packages however, is not such a good idea.

---

### Post by humphreybc on 2009-09-29
Generally just closing the terminal while it's downloading will pause it, and it'll start downloading from where it left off next time.

Closing the terminal while it's INSTALLING packages however, is not such a good idea.

---

### Post by vipulkelkar on 2009-09-29
ok thanks..ya its not a good idea to close it while a package is getting installed,
but the upgrading taks takes time..n if suppose i need to pause..it'll resume from the last interrupted point itself ??

---

### Post by humphreybc on 2009-09-29
Yes, as long as you close it while it is downloading packages, not installing them.

If you close it while it is installing, then you'll get an error where Ubuntu can't get a lock on apt-get, and you'll have to reconfigure apt or restart the computer and start from the beginning and install them again.

But if you close it while it's downloading, then it'll just resume from wherever it left off next time you run sudo apt-get upgrade

---

### Post by misfitpierce on 2009-09-29
Closing while downloading sometimes can lock up the root privileges thing or it has for me once or twice before... I would recommend CTRL+C or something along those lines before just force closing the terminal.

---

