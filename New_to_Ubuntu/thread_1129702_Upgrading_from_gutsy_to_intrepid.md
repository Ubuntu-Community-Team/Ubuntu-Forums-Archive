---
title: "Upgrading from gutsy to intrepid"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by dhirajkhanna on 2009-04-18
Hi I am trying to upgrade from gutsy to intrepid. This is the outcome of```
sudo apt-get upgrade
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libffi4: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
E: Unmet dependencies. Try using -f.
```

When I do ```
sudo apt-get -f install 
```, This is what I get

```
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-style-crystal_1%3a2.4.1-1ubuntu2.1_all.deb
 /var/cache/apt/archives/openoffice.org-style-human_1%3a2.4.1-1ubuntu2.1_all.deb
 /var/cache/apt/archives/python-uno_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-writer_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-calc_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-base-core_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-impress_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-draw_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-kde_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-math_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-common_1%3a2.4.1-1ubuntu2.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Help will be appreciated

---

### Post by mikewhatever on 2009-04-19
You can't upgrade directly from Gutsy to Intrepid, since Hardy is in between. In my opinion, it's easier to reinstall, then go Gutsy->Hardy->Intrepid.

---

### Post by dhirajkhanna on 2009-04-19
Guess you are right. I did a fresh install but have fallen into deeper trouble!! [http://ubuntuforums.org/showthread.php?t=1100285](http://ubuntuforums.org/showthread.php?t=1100285)

I had faced this about a month back and its now back to haunt me.

---

