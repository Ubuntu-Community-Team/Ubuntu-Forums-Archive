---
title: "Cant remove a program(Ive searched)"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by willhe3rd on 2010-04-12
Installed azureus vuze from the terminal. Im not thrilled with it and want to remove it. I used the comand
```
 sudo apt-get remove azureus
```and
```
sudo apt-get remove vuze
```it then listed a buch of files no longer needed so I erased them as well. The program is still there and operational. I tried the above again and it says that they dont exsist. I even looked for them in synaptic and the software center with no luck but I expected that What am I missing?

---

### Post by r-senior on 2010-04-12
Looks like it's not just you ...

[http://ubuntuforums.org/showthread.php?t=818829](http://ubuntuforums.org/showthread.php?t=818829)

I'd give it the benefit of doubt and try:

$ sudo apt-get remove --purge azureus 
$ sudo apt-get remove --purge vuze

If that doesn't zap it, check through the lists of files in the two packages and carefully delete them:

[http://packages.ubuntu.com/karmic/all/azureus/filelist](http://packages.ubuntu.com/karmic/all/azureus/filelist)
[http://packages.ubuntu.com/karmic/all/vuze/filelist](http://packages.ubuntu.com/karmic/all/vuze/filelist)

---

### Post by halitech on 2010-04-12
how did you install the program to start with? If you didn't install it from Synaptic or the package manager, it won't be able to remove it.

---

