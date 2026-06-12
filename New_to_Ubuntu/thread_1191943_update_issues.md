---
title: "update issues"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by shifty_powers on 2009-06-19
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

is the output when i try

```
sudo apt-get update
```

same with update manager... (see screenshot)

any ideas?

edit: ignore my profile, currently using 9.04 32-bit...

---

### Post by michy99 on 2009-06-19
Try this:```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
sudo apt-get update
```

---

### Post by shifty_powers on 2009-06-19
tried that, didn't work.

solved it by deleting the lot of them and updating again.

cheers for the suggestion mind :D

---

