---
title: "Can't upgrade to 9.10!"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2009-12-02
Hello all. I'm having trouble upgrading to 9.10. Update Manager tells me I'm up to date, and trying to use the terminal gives me this:

```
Setting up ezmlm-browse (0.10-2) ...
make: Entering directory `/usr/lib/ezmlm-browse'
python -c '__import__("commands/lists")'
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: Import by filename is not supported.
make: *** [commands/lists.pyc] Error 1
make: Leaving directory `/usr/lib/ezmlm-browse'
dpkg: error processing ezmlm-browse (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ezmlm-browse
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by jrrader on 2009-12-02
Do yourself a favor and don't upgrade.  I'm sure someone can figure out this problem - but if you upgrade from 9.04 to 9.10 you're going to have a whole new set of problems.  

I'm not saying not to use 9.10 - I do - but a clean install will save you a lot of other problems to fix.

---

### Post by Julita on 2009-12-02
In order to upgrade a distro using an update manager, you should run in the terminal 
```
 update-manager -d
```

You will see that new version is available and you will be able to upgrade.

---

