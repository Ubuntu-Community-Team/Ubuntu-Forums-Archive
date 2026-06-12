---
title: "Ubuntu kernel sources?"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by Fanatico on 2011-01-20
I've installed latest Ubuntu version from Live CD.

Now I need to rebuild kernel, so I have the following questions:

1. Does the installer from Live CD include kernel sources with all Ubuntu patches and corresponding configuration file (.config) in its standard installation or not? If yes, in which directory?

2. If no, where can I get kernel sources with all Ubuntu patches and corresponding configuration file (.config)

Thanks

---

### Post by oldos2er on 2011-01-20
I think ```
apt-get source linux-source
``` will do what you need.

---

### Post by Fanatico on 2011-01-21
> **oldos2er said:**
> I think ```
apt-get source linux-source
``` will do what you need.

In what directory will this command install sources? What about .config file?
Could you confirm that standard Ubuntu Live CD doesn't install kernel sources by default?

---

### Post by NightwishFan on 2011-01-21
I am fairly sure the live CD does not have kernel sources only headers. As for the config file I am not actually sure where it is located in the source packages if at all. They might just diff it in when you get a specific source package. I have a kernel compile tutorial here, however there are other ways to use the source. (Also ignore the middle part about the CK patches).

[http://ubuntuforums.org/showthread.php?t=1637004](http://ubuntuforums.org/showthread.php?t=1637004)

---

### Post by oldos2er on 2011-01-21
> **Fanatico said:**
> In what directory will this command install sources? What about .config file?


They will be installed to the current directory. I don't know about the .config file.

Maybe this will help: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

