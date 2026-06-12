---
title: "Is reloading Synaptic the same as updating the repositories?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by killbydemons on 2008-12-24
I'm not sure what repositories are..is it the list of software/updates presented in Synaptic?

---

### Post by taurus on 2008-12-24
Repositories are resided in /etc/apt/sources.list.  Add/Remove & synaptic are both reading that file.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by ajgreeny on 2008-12-24
Repositories are like digital warehouses sitting on a computer in South Africa, UK, America, etc etc.   They contain Ubuntu or (other distro if you use another) application packages which you use to install programs on to your computer, rather like the setup.exe files you will probably have used in windows.  It means that installing almost anything you wish is so much easier for ubuntu than it is for windows, because the search for it is so much simpler.

To update the repositories you need to click the reload button in synaptic or use ```
sudo apt-get update
``` in terminal.  ```
sudo apt-get upgrade
``` will then make sure you have the latest of everything for your version of Ubuntu, the same as using the Update manager, or synaptic.

---

### Post by bodhi.zazen on 2008-12-24
See also :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by snova on 2008-12-24
Despite the many helpful answers already presented, I believe there is still some ambiguity to be cleared up...

A "repository" is just a website with packages. The site is laid out in a particular format so that package management software on your computer can find a particular one on the website, download it, and install it.

Ubuntu keeps lists of packages that are on each repository. For example, if you were to enable the Universe repositories, you'd have to download a list from that site. This is what the Reload button does- it fetches updated package lists.

A list of enabled repositories is kept in /etc/apt/sources.list, but you don't need to manipulate it directly, as you can also use System -> Administration -> Software Sources.

---

