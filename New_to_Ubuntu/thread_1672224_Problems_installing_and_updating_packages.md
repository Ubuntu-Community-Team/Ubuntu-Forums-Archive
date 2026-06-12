---
title: "Problems installing and updating packages"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by darthspringbok on 2011-01-20
When I try and install updates or any package into 10.10 I get an error:

"The index packages are currently changed by apt-get"

It  will sometime just work after a reboot or 2 but sometimes I just cannot  get anything installed. I cannot be certain but I'm sure this started  after I did a manual install (i.e. command line, not through package  manager) of wine 1.3 a few weeks back.

---

### Post by lbarnes on 2011-01-20
Please post the output of this:
```
sudo apt-get update && sudo apt-get upgrade
```

---

