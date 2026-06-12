---
title: "unable to download updates"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-11-26
i keep getting the error message that ubuntu cant authenticate packages. i downloaded 10.10 on this computer a few months ago and have not used it sence then. i have a lot of packages to update but it wont work. it asks me to do the partial upgrade because it is trying to upgrade to the next distribution.  i have also tried alt+f2 but that asked me if i wanted to upgrade to 11.04 is there anything else i could try?

---

### Post by marbertone on 2010-11-26
Try to write in a terminal:
```
sudo apt-get upgrade 
sudo apt-get update 
```
it usually gives you more permission than the graphical UI.
Cheers,
M.A.

---

### Post by plucky on 2010-11-27
> **marbertone said:**
> Try to write in a terminal:
```
sudo apt-get upgrade 
sudo apt-get update 
```
it usually gives you more permission than the graphical UI.
Cheers,
M.A.

Do the "update" first as that reloads the index files and the "upgrade" actually installs the upgrades.

Post the output from those commands if there are any errors.

> i keep getting the error message that ubuntu cant authenticate packages. i downloaded 10.10 on this computer a few months ago and have not used it sence then. i have a lot of packages to update but it wont work. it asks me to do the partial upgrade because it is trying to upgrade to the next distribution. i have also tried alt+f2 but that asked me if i wanted to upgrade to 11.04 is there anything else i could try? 

What command did you use as it should not be offering the upgrade to 11.04 ,which is still in alpha testing phase? 


Good Luck

---

