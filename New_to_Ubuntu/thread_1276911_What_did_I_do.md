---
title: "What did I do?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by elurban3d on 2009-09-27
Tried to install kubuntu and xubuntu as separate OS running sudo aptitude but now all the comes up is kubuntu.  I expected to be given an option at startup to boot into ubuntu, kubuntu or xubuntu.

I am trying to see which of the three performs better on my computer.

---

### Post by halitech on 2009-09-27
if you installed them using sudo aptitude you didn't install them as seperate OSes, you installed the Desktop Environments into a single OS. When you log in, check on sessions and you should see each option listed there. Select the one you want to try and log in.

---

### Post by gali98 on 2009-09-27
To install them as separate OSes (i.e. separate installations in the grub boot menu) you would have to install again with an ubuntu (or kubuntu/edbuntu) install disk, and when repartition your disk with the installer.
Kory

---

### Post by elurban3d on 2009-09-27
bleck.  how do I get rid of them?

---

### Post by gali98 on 2009-09-27
Lol, I know what you mean. You end up having a million programs installed.
The best way would be to go into synaptic package manager.
Then go to Edit-> mark packages by task.
From there deselect the packages (i.e desktops) you don't want then just apply the changes with synaptic and reboot, and everything should be good.
You might need to run 
sudo apt-get autoremove 
to clean up everything.
Kory

---

### Post by sandyd on 2009-09-27
```

sudo apt-get remove kubuntu-desktop xubuntu-desktop
sudo apt-get autoremove

```

---

