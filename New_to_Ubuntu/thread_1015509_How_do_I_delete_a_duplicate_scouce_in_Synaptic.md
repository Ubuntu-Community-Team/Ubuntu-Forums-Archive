---
title: "How do I delete a duplicate scouce in Synaptic??"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-18
When I go into Synaptic sometimes I get the following pop-up ERROR (it seems to only come after a restart/new boot:

W: Duplicate sources.list entry [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Packages (/var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Translation-en_GB (/var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_hardy_universe_i18n_Translation-en%5fGB)

To me, as I read them, they are two different sources and not duplicate sources - but then, what do I know - less than nothing when it comes to working with Linux.

My question is, where and how do I delete one of these sources, I don't seem to be able to find them anywhere??

---

### Post by taurus on 2008-12-18
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Therion on 2008-12-18
System/Administration/Software Sources.
"Third-Party Software" tab.
Un-check any duplicated sources you find listed.

---

### Post by thadacto on 2008-12-18
Thanks taurus, you seem to be always coming to my rescue. I'm working on it - marking it solved.

---

