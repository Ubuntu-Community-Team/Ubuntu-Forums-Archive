---
title: "Cannot run update"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by darthspringbok on 2011-01-20
When I try and install updates or any package into 10.10 I get an error:

"The index packages are currently changed by apt-get"

It will sometime just work after a reboot or 2 but sometimes I just cannot get anything installed. I cannot be certain but I'm sure this started after I did a manual install (i.e. command line, not through package manager) of wine 1.3 a few weeks back.

---

### Post by Rubi1200 on 2011-01-22
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal and run the following commands:

```
sudo dpkg --configure -a
```

Also, post the output of this:

```
cat /etc/apt/sources.list
```

---

### Post by darthspringbok on 2011-02-04
I just reinstalled ubuntu. no problems now.

---

### Post by Rubi1200 on 2011-02-04
Glad you got things worked out.

Enjoy!

---

