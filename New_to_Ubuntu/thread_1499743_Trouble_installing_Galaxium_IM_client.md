---
title: "Trouble installing Galaxium IM client"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by William S on 2010-06-02
Hello!
I have a problem installing Galaxium IM client. As it is not in Ubuntu resiptories I have to compile it from source. The configscript works, but when I get to MAKE I get this error message:
```

/Utilities/ArgumentUtility.cs(284,36): error CS8244: The `is' operator cannot be applied to an operand of a static type
Compilation failed: 1 error(s), 0 warnings
make[2]: *** [../../build/Galaxium.Core.dll] Error 1
make[2]: Leaving directory `/home/william/s/galaxium-0.7.4.1/src/Galaxium.Core'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/william/s/galaxium-0.7.4.1/src'
make: *** [all-recursive] Error 1



```

Anyone have solution for this?

---

### Post by LowSky on 2010-06-02
try ```
sudo make
```

---

### Post by William S on 2010-06-02
> **LowSky said:**
> try ```
sudo make
```

I still get the same error.

---

### Post by LowSky on 2010-06-02
I found this error searching google, its from a year ago
[http://code.google.com/p/galaxium/issues/detail?id=332](http://code.google.com/p/galaxium/issues/detail?id=332)


there is repo for Ubuntu 9.04 it might work for you, [http://code.google.com/p/galaxium/wiki/InstallUbuntuJaunty](http://code.google.com/p/galaxium/wiki/InstallUbuntuJaunty)


Add the following lines to /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/galaxium/ubuntu jaunty main
deb-src http://ppa.launchpad.net/galaxium/ubuntu jaunty main
```

Type the following commands in a terminal:

```
sudo apt-get update
sudo apt-get install galaxium-svn
```

---

