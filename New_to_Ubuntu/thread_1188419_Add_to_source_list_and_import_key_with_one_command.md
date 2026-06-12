---
title: "Add to source list and import key with one command?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-06-15
If I have the this:

```

deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
```

And the link to key, can I adapt it to something like this?

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

---

### Post by oldos2er on 2009-06-15
You can use && to string two or more commands together e.g.
```
sudo apt-get update && sudo apt-get upgrade
``` If one of the commands fails for some reason, the subsequent command(s) will not run; in other words, one command must be successfully run before the next will work. Kind of a fail-safe thing.

---

### Post by Sup3r3g0 on 2009-06-15
Okay thanks

---

