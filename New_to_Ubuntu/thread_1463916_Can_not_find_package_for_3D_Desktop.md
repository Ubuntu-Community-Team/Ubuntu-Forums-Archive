---
title: "Can not find package for 3D Desktop?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-27
This is what I am getting after the first step at trying to use the 3D desktop from this thread:
[http://ubuntuforums.org/showthread.php?t=100169](http://ubuntuforums.org/showthread.php?t=100169)

I get this:

joe@laptop:~$ sudo apt-get install 3ddesktop
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package 3ddesktop

Does anyone know why? I think I have all the repositories set right.

---

### Post by da burger on 2010-04-27
This is just a guess but that is an old tutorial so the package might have been removed by now. That's just a guess though.

---

### Post by NightwishFan on 2010-04-27
You can search for software in the Software Center or Synaptic. The above poster is probably correct.

---

### Post by mk1w86 on 2010-04-27
Do you have Compiz working?  I'm sure you can achieve a similar effect using that.

To adjust Compiz settings further than the default Ubuntu options you need to install the CompizConfig Settings Manager by running:

```
sudo aptitude install compizconfig-settings-manager
```

---

### Post by joenewtzie on 2010-04-27
> **mk1w86 said:**
> Do you have Compiz working?  I'm sure you can achieve a similar effect using that.

To adjust Compiz settings further than the default Ubuntu options you need to install the CompizConfig Settings Manager by running:

```
sudo aptitude install compizconfig-settings-manager
```

Just found that and I am now experimenting with it now, kind of hard to figure some of it out, but i'll manage.  thanks for the help everyone!

---

### Post by eriktheblu on 2010-04-27
> 3d-desktop has not been in development for some time. Check out Compiz though. It is a compositing window manager that will give you a 3d desktop in a much more dynamic, robust and not to mention very cool way. 
I think development pretty much stopped 6 years ago.

---

