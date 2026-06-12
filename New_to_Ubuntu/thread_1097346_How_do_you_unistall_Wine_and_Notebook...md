---
title: "How do you unistall Wine and Notebook..?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-03-15
Accidentally installed Notebook & Wine...  

How do I get rid of them..?

---

### Post by spcwingo on 2009-03-15
Open a terminal and copy/paste this:

```
sudo apt-get remove --purge wine notebook-gtk2 && sudo apt-get autoremove
```

This will remove the programs, config files for those programs, and unused dependencies brought in by the installation of those programs.

---

### Post by DonaldJ on 2009-03-15
Got it.. Thanks...

---

