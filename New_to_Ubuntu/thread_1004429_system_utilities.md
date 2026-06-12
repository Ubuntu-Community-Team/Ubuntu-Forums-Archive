---
title: "system utilities"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by paulm2008 on 2008-12-07
Good Afternoon.  While keeping upto date with all the updates with Kubuntu. When I boot my system the grub loader options are getting quite unmanagable i.e. I have a list of about 15 differing boot options, which I can see could multiply even firther.  I'm wondering if there is a simple utility which in effect will remove the older versions of these Kernals, without the risk of crashing my installation [if for example this is done through a package manager].

Additionally is there also a utility which would keep a control of any rementant or junk files left on my system following installation/removl of packages

Any information on system utility cleaners would be very helpful - thank you


Regards, Paul.

---

### Post by fooman on 2008-12-07
there is an app available from synaptic called "startup-manager" that will control how many kernels are visible at boot quite easily.

or you can grab it in a terminal with this command:

```
sudo apt-get install startupmanager
```

start it in the terminal with:

```
sudo startupmanager
```

limit the visible kernels under the "advanced" tab.

and here is a really nice guide for cleaning things up:

[http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning](http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning)

---

### Post by _sAm_ on 2008-12-07
You can remove old kernels you don't longer use with Synaptic. 

You can read how to here; [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

