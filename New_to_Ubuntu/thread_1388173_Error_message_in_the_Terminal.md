---
title: "Error message in the Terminal"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Peterfc on 2010-01-22
Hi all

I am trying to reinstall Gimp On the Gimp site it says to [COLOR="Blue"]apt-get install gimp[/COLOR] in the terminal. When i try this i get the error message below

The reason to reinstall Gimp is for some reason it is not opening and i have work to do with Gimp.

Thanks for reading this cry for help

peter@peter-laptop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
peter@peter-laptop:~$

---

### Post by phidia on 2010-01-22
Try > sudo apt-get install gimp

---

### Post by epicoder on 2010-01-22
You must be the superuser to install packages.
sudo [command]

To reinstall gimp, you must run first:
sudo apt-get remove gimp
Then run:
sudo apt-get install gimp.

---

