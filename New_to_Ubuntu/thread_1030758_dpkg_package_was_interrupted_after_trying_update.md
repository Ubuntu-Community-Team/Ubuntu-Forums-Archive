---
title: "dpkg package was interrupted after trying update"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by hens on 2009-01-04
I installed Ubuntu 2 days ago,after logging on it get the popup telling me that i have software that need to be updated, i proceed to update the software then i get this error: dpkg was interrupted, you must manually run 'dpkg --configure -a to correct the problem. Since i am new i went to the terminal after typing help, and  reading some of the information. i tried sudo apt-get install dpkg --configure -a, it gives me an error saying that the --configure is not a recognizable command line argument. i tried su to get to root, when i put in my password it tells me that the password is incorrect and root does not exist. i am the only one using this computer, and i only have one password. when i try to install root(apt-get install root -bin it tells me that i need to install 'dpkg --configure -a in order to get any further. Also, i cannot open firefox, it tries to start up and just closes all by itself. Anyone have any ideas what is going with this install. i am using the latest Ubuntu

Thanks

---

### Post by semi_fiction on 2009-01-04
Hi!
Go to the terminal and type this:
```
sudo dpkg --configure -a
```
then hit enter, type your password, then hit enter again.
Then you should be able to update.

---

