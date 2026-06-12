---
title: "How to print info from sysinfo?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by ShadowTek on 2009-08-17
I'd like to print the information found in the sysinfo GUI.

How do I get this information from/in the command line?

---

### Post by arochester on 2009-08-17
I don't know about sysinfo, but you can create an html file from lshw with the command
> $sudo lshw -html > your-file-name.html See [http://embraceubuntu.com/2007/02/18/find-hardware-specs-details-on-your-computer/](http://embraceubuntu.com/2007/02/18/find-hardware-specs-details-on-your-computer/)

---

### Post by aesis05401 on 2009-08-17
Hello, 

From the package description it appears that sysinfo pulls information from a number of places.  Here is a brief list of commands to find the information referenced in the sysinfo description:
```

# System... Linux release/kernel
uname -a

# Package versions
dpkg -l

# CPU information
less /proc/cpuinfo

# RAM information
less /proc/meminfo

# All the assorted hardware information can be sorted with lshw
sudo lshw

```

---

### Post by credobyte on 2009-08-17
Menu contains "Save" option - save it, print it, forget about it.

---

### Post by ShadowTek on 2009-08-17
uname, that's the one.

That command name is so unintuitive and hard to remember if you happen to forget it.

Thanks

---

