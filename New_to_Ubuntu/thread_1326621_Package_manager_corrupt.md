---
title: "Package manager corrupt"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by duttydea on 2009-11-14
My Package manager is messed up,

It keeps asking to uninstall a package for my brother printer, them complains that it cant find the package.

whenever i download the package and try to install it it says that the package is corrupt or i don't have access!!

I have tried a few way to repair the package manager using the CD & Force Remove!!

what can i do!!?

thanks in advance

---

### Post by s3a on 2009-11-14
sudo apt-get install -f or sudo dpkg --configure -a perhaps?

Also, if you're trying to install a .deb with missing dependencies; right after you do sudo dpkg -i *.deb (assuming your .deb is in the home directory and is the only .deb file there), you have to do sudo apt-get install -f and it will obtain the dependencies for you.

---

### Post by duttydea on 2009-11-14
Thanks for the advice,

I tried this: $ sudo apt-get install -f 
and got

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ql550cupswrapper needs to be reinstalled, but I can't find an archive for it.


Where would i need to put the file in-order for it to be reinstalled?

its been bugging me for a while & now i wanna upgrade to 9.10

thanks

---

