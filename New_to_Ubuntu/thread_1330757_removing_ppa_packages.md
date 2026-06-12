---
title: "removing ppa packages"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by gorgon on 2009-11-18
ajaja,
when trying to fix this problem
[http://ubuntuforums.org/showthread.php?p=8342658](http://ubuntuforums.org/showthread.php?p=8342658)
I took the risk of trying to install some packages from a ppa on launchpad to get a newer version of the program that was the issue.

Now, I got two versions of that program

```
grgn@ubuntu:~$ apt-show-versions -a jackd
jackd 1.9.3 install ok installed
jackd 0.116.1-3ubuntu3 jaunty no.archive.ubuntu.com
jackd 1.9.3            jaunty ppa.launchpad.net
jackd/jaunty uptodate 1.9.3
```

and they conflict.

so, how can I get back to the state before tampering? removing the ppa packages (how do I know what depends where?) and reinstalling the previous libs?

---

### Post by spikyjt on 2009-11-18
I don't think you have two versions installed. That isn't possible, unless the ppa package is seriously mis-configured. apt-show-versions is just showing what versions are available. As the output says, version 1.9.3 is installed.

If you want to completely remove the ppa version, do ```
apt-get purge jackd
``` then remove the ppa from the sources list and ```
apt-get update
apt-get install jackd
```

If you can't purge jack because of dependencies, then you could try removing the ppa from the sources list and then ```
apt-get update
apt-get --reinstall install jackd
```

good luck

---

### Post by gorgon on 2009-11-18
> I don't think you have two versions installed
ok, this is odd since when I do:

```

grgn@ubuntu:~$ jackd
jackd 0.116.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
 ...


```

and apt-show-versions says 1.9.3 is installed

hm.

---

### Post by spikyjt on 2009-11-18
note version installed is 0.116.2 not 0.116.1 as per ubuntu repo. The ppa package has called itself version 1.9.3, but it would seem odd that there would be such a huge jump in version numbers, when ubuntu is a pretty bleeding edge distro wouldn't it? In fact the very latest release of jack is version 0.118. 1.9.3 is the latest release of jack 2 (nice easy to follow release versions ;) ) but this package seems to contain version 0.116.2 of jack. So no you don't have two versions installed (honestly it just isn't possible if you used the package manager).

---

### Post by gorgon on 2009-11-18
ah, so jack and jack2.. but they both use the same name for the program

ok, I got around it by going in to synaptics and removed the packages there, then removed the repositories of the ppa, then reinstalled the packages from the distribution.

tada.

thanks for the support skikyjt!

---

