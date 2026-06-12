---
title: "Adobe Flash Problem"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by tmos22 on 2009-05-04
Hey guys , im a noob at this so go easy! I have just installed ubuntu and i want  to install Adobe flash player so i can view videos on youtube etc i tried to install the version for Ubuntu but i got this error "Error: Dependency is not satisfiable: libcurl3"

---

### Post by jbrown96 on 2009-05-04
Need some more info about your system. could you post the output of the following command from a terminal (apps-->accessories) ```
uname -a
```

---

### Post by tmos22 on 2009-05-04
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by stchman on 2009-05-04
Do the following:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by tmos22 on 2009-05-04
> **stchman said:**
> Do the following:

```
sudo apt-get install flashplugin-nonfree
```

Ok , i have done that , and then it asks for my password but when i go to type my password, nothing happens, its just wont type anything:confused:

---

### Post by SuperSonic4 on 2009-05-04
It is typing but it won't show it. Type as normal and press enter

---

### Post by gandaran on 2009-05-04
> **tmos22 said:**
> Hey guys , im a noob at this so go easy! I have just installed ubuntu and i want  to install Adobe flash player so i can view videos on youtube etc i tried to install the version for Ubuntu but i got this error "Error: Dependency is not satisfiable: libcurl3"
run **sudo apt-get update** before installing the flash package

---

### Post by tmos22 on 2009-05-04
It worked after i updated, you guys are awesome, thanks for everyones help, i will have plenty more questions real soon lol

---

### Post by kansasnoob on 2009-05-04
> **tmos22 said:**
> Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

OK, that's Jaunty. As far as the password, that's already been explained. It's not displayed. That's common behavior actually.

Anyway I've found flash in Jaunty to be this simple:

Go to System > Administration > Synaptic Package Manager and click on Search (not quick search or rebuilding search!), then type **flash**, then you should see only packages related to "flash".

That will begin with "adobe-flashplugin" and end with "yamdi". The only two packages that should be installed are ubuntu-restricted-extras and adobe-flashplugin!

If gnash or any of the swfdec-* packages are installed mark them for "complete removal" (the equivalent of purge remove). Obviously mark ubuntu-restricted-extras for installation, then restart Firefox and you should have a working flash plugin!

I've also found "Flashblock" to be very helpful. It replaces flash objects with a "button", so flash doesn't gobble up as much resources and you can always view any flash object just by clicking on the 'button". But the version of Flashblock in synaptic is archaic so go to Firefox & Tools > Add-ons > Get Add-ons, then search for and install Flashblock (current version 1.5.10). Then you'll be prompted to restart Firefox.

---

