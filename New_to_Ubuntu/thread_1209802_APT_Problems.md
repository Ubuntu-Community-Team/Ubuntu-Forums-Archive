---
title: "APT Problems"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-07-10
Hello all. I'm experiencing  a few problems with APT - when I try to apt-get install anything, or do so via adept/whatever, it fails and gives me an error message of 'You are holding broken packages.'

Anyone know what might be wrong? My meager knowledge has no idea :P

---

### Post by unutbu on 2009-07-10
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo apt-get -f install
```

This will tell apt-get to fix any packages with broken dependencies.

If it does not solve the problem, please post the terminal output.

---

### Post by Azhtabak on 2009-07-10
Doesn't do anything:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amarok-common libloudmouth1-0 ruby1.8 ruby libruby1.8
  stardict-plugin-gucharmap
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Western Digital on 2009-07-10
Then do what it says: 

```
apt-get autoremove
```

---

