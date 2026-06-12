---
title: "can't open my synaptic package manager"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by xnipher on 2010-11-01
Whenever I open my Synaptic Package Manager and the application opens.
and Another pop-up saying Error occured:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

i try to run sudo dpkg --configure -a
nothing happens. anyone help?

---

### Post by garvinrick4 on 2010-11-01
Did all go fine on install? Try:
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```
Now go back to Synaptics and see what happens.

---

