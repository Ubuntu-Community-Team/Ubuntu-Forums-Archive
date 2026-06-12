---
title: "Package manager crashed!"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by 7mm on 2011-05-01
**Hi there, I've just installed Ubuntu 11.04. Tried installing nvidia drivers but failed. Now I get the error message when launching Syanptic Package Manager as below, please help!**

> [I][COLOR="Blue"]E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/COLOR][/I]

---

### Post by oldos2er on 2011-05-01
Open the file in gedit (text editor) ```
gksu gedit /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-natty.list
```The file should look like this:

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) natty main  
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) natty main

Save the file, exit, and run ```
sudo apt-get update
```

---

### Post by 7mm on 2011-05-04
**That's good, it worked. Thank you "oldos2er" for your valued time & good support, CHEERS!**

---

