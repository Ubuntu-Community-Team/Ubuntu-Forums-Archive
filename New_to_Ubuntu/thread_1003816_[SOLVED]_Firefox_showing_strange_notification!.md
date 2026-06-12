---
title: "[SOLVED] Firefox showing strange notification!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by bhadotia on 2008-12-06
I reinstalled my ubuntu today. I had backed up all my archives in a separate partition and then copied them to /var/cache/apt so that I don't have to download all of them again. And did [this]("http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html").
During the process of :
```
sudo apt-get dselect-upgrade
```
I received a panel icon notification to restart firefox and I did that (the apt-get process was not complete yet). 
 
Now, after everything has completed (the installation and configuration process), I am still getting a pop on the top of firefox window which says: Your browser has been updated and needs to be restarted". And when I click the "Restart" button next to the above sentence And firefox restarts, I still get the same notification. 
Any ideas on what is causing this.

Many thanks in advance):P

---

### Post by gettinoriginal on 2008-12-06
Clear all Private Data and cache and restart it again, that may clean it up.

---

### Post by bhadotia on 2008-12-07
> **gettinoriginal said:**
> Clear all Private Data and cache and restart it again, that may clean it up.

Actually, that did solve the problem. While that did not work when I deleted the whole profile (~/.mozilla/firefox). So i got a little confused. Funny, Igot so confused that clearing the private data etc. didn't even hit my mind:p

Well, thank you very much.:D

---

### Post by gettinoriginal on 2008-12-07
you are welcome, and please mark this as solved. :p

---

