---
title: "synaptic package not working anymore"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by skilgannon82 on 2011-06-08
i just saw below someone with a similar problem but their solution does not help me 
i cannot get any packages at all anymore or updates and when i try it says to report this problem

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

i have no idea what it means and dont know who im supposed to report it to

---

### Post by wolfen69 on 2011-06-08
```
sudo rm -rf /var/lib/apt/lists/*
```
then
```
sudo apt-get update
```

---

### Post by skilgannon82 on 2011-06-08
excellent thank you

---

