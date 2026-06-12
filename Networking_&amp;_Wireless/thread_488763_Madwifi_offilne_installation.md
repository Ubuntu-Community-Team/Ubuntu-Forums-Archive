---
title: "Madwifi offilne installation"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by IFailAtLinux on 2007-06-30
I have wifi card PC-6860 which is said to work with linux with madwifi driver. And I'm pretty sure I saw post of someone with Feisty who got it working.

Unfortunately right now I'm completely cut off from net when I boot into linux so apt-getting anything is out of question, and all tutorials that dealt with .deb files for madwifi did apt-getting sooner or later, or used something else that was supposed to download stuff from net. When it was just apt-getting I would dl stuff manually on windows and then try going with tutorial, but in all cases I came to place where it wanted to use itnernet before drivers were installed.

Is it even possible to get that drivers installed completely offline and does anyone know a way to do it?

---

### Post by spd106 on 2007-07-02
The madwifi driver is included in a default install within the linux-restricted-modules package. You should be able to activate it through the restricted driver manager.

If it's not working could you please post the output of these commands?
```
lspci
```
```
sudo lshw -class network
```

---

