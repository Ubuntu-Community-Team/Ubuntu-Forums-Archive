---
title: "Issues with GNUNET Configuration (rights issue)"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by CSHANKY on 2010-04-16
Can't start the config wizard - says "Failed to run the configuration tool (gnunet-setup). You don't have rights to write to the provided config file"

Config file used: /etc/gnunetd.conf

---

### Post by Jon Monreal on 2010-04-17
You could try going to a terminal and typing
```
sudo grunet-setup
```

Alternatively, you could CHMOD the file, but the first method is easier so I would try that first.

---

### Post by arclightfire on 2010-04-19
> **Jon Monreal said:**
> You could try going to a terminal and typing
```
sudo grunet-setup
```

Alternatively, you could CHMOD the file, but the first method is easier so I would try that first.

Also if you are not in the right directory, this wont work, so I typed:
```
cd /
```
```
cd etc
```
Then typed...
```
sudo grunet-setup
```

Next you might find you need to install the gnunet-server too...
[http://ubuntuforums.org/showthread.php?t=1371896](http://ubuntuforums.org/showthread.php?t=1371896)

---

