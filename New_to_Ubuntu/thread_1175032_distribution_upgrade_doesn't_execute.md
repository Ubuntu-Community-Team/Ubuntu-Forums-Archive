---
title: "distribution upgrade doesn't execute"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by ni ni on 2009-05-31
hi all

i get a message that says i can only have a partial upgrade.  I enter my password and it tells me 2 packages are to be removed, 7 are to be installed and 80 are to be upgraded.

i press "start upgrade", but it then disappears till the next time, where it the same story again so no upgrades get applied.

any ideas what's up?


thanks v much xxxxxxxxxxxxxxxxxxxxxx

---

### Post by Random-penguin on 2009-05-31
Hi again! It is usually better not to do a distro upgrade but to re-install from scratch (first making sure you've backed up everything important). This makes sure everything is set up properly for your version of Ubuntu. If you don't like the idea of re-installing every 6months try the long term support version: Ubuntu 8.04 is the current LTS. Hope this helps!

---

### Post by ni ni on 2009-05-31
oh that really helps!

I'm gonna do a re-install from scratch tomorrow so!


thanks xxxx:KS:KS:KS:KS

---

### Post by Random-penguin on 2009-05-31
Glad to help and hope all goes well!!!!!!! ;)

---

### Post by Diabolis on 2009-05-31
Try this in a terminal (Accessories / Terminal) :
```
sudo apt-get update
apt-get dist-upgrade
```

It will ask for your password, but It won't display any characters as you type them in, thats normal. Ubuntu is designed to be upgradeable and most of times it will work. Sometimes error messages are only displayed in the terminal, thats why you should try this, to see which is the exact problem.

---

