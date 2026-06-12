---
title: "Error with software center"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by miji.nyan on 2010-11-02
This happened with software installer, help.
The installation could have failed because of an error in the corresponding software package or it was canceled in an unfriendly way. You have to repair this before you can install or remove any further software

---

### Post by arochester on 2010-11-02
Open a Terminal and try each of the following commands in turn:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update

Try again...

---

### Post by cariboo on 2010-11-02
Is that the only message you got, or is there more to it?

To solve your problem, go to System->Administration->Synaptic Package Manager->Edit->Broken Packages. This will show you which packages need to be removed. Remove them and you should be OK to go.

---

### Post by miji.nyan on 2010-11-02
> **arochester said:**
> Open a Terminal and try each of the following commands in turn:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update

Try again...
Thank you so much! Terminal commands worked like a charm

---

