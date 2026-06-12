---
title: "How to uninstall 3rd party software from 10.04?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Viau on 2010-05-26
Hey, I have recently installed daimonin on my 10.04 netbook and I encountered a bug that requires me to uninstall the software for reinstallation. I cannot find where I can do that on this 10.04 ubuntu :(

Can someone help me please!!
Thanks

---

### Post by SlidingHorn on 2010-05-26
```
sudo apt-get remove daimonin
``` 

or, if you want to delete the configuration files as well:

```
sudo apt-get remove --purge daimonin
```

---

### Post by Viau on 2010-05-26
> **SlidingHorn said:**
> ```
sudo apt-get remove daimonin
``` 

or, if you want to delete the configuration files as well:

```
sudo apt-get remove --purge daimonin
```

E: couldnt find package daimonin

---

### Post by Skorzen on 2010-05-26
Is that package from the repositories?

Where do it has files installed?
```
dpkg -L example
```

---

### Post by gandaran on 2010-05-26
what type of package file was it that you used to install?
if it was .deb use synaptic to remove it, if something else you must read the package instructions for removal.

---

### Post by Viau on 2010-05-26
> **Skorzen said:**
> Is that package from the repositories?

Where do it has files installed?
```
dpkg -L example
```

it is a package I downloaded from their website.
It is a .package...
first Time I've seen this.

---

### Post by Viau on 2010-05-26
Okay, I have uninstalled it that way: I double clicked the installation package and it uninstalled before reinstalling, so I clicked again and I unplugged my laptop right when it was uninstalled. Now I will try this
[http://www.linux-solved.com/post/SOLVED-HOWTO-Install-daimonin-online-mmorpg-client-42893.html](http://www.linux-solved.com/post/SOLVED-HOWTO-Install-daimonin-online-mmorpg-client-42893.html)

---

