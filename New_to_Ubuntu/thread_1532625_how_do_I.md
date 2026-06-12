---
title: "how do I???"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by k33bz on 2010-07-16
How do I take care of this:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf), E:Error occurred while processing mysql-common (NewFileDesc2), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'
```

Cant run synaptic or package manager at the moment because of this.

---

### Post by Gone fishing on 2010-07-16
Have a look  this:

[http://www.bigtechnologiesinc.com/big-technologies-blog/35-linux/50-dynamic-mmap-apt-get](http://www.bigtechnologiesinc.com/big-technologies-blog/35-linux/50-dynamic-mmap-apt-get)

---

### Post by jtarin on 2010-07-16
You can set it to how much you like but keep in mind not to let it fill /var or worse /.
"apt-get clean" or "aptitude clean" now and then would clean up the /var/cache/apt/archives so you can manage with a lower limit.

---

### Post by k33bz on 2010-07-16
> **Gone fishing said:**
> Have a look  this:

[http://www.bigtechnologiesinc.com/big-technologies-blog/35-linux/50-dynamic-mmap-apt-get](http://www.bigtechnologiesinc.com/big-technologies-blog/35-linux/50-dynamic-mmap-apt-get)
That was perfect, followed the tut exactly. However I still see the warning sign in my task bar. I can use update package manager and synaptic manager.



> **jtarin said:**
> You can set it to how much you like but keep in mind not to let it fill /var or worse /.
"apt-get clean" or "aptitude clean" now and then would clean up the /var/cache/apt/archives so you can manage with a lower limit.

Gotcha, did both.

---

