---
title: "trouble installing windows xp on ubuntu using VirtualBox"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by john_galt on 2008-12-28
So, I want to install some windows-only softwares and I come to know about VirtualBox. Now, while installing windows xp, I refer an iso file to the virtualmachine and after I press 'Start' it shows up this message: FATAL: INT18: BOOT FAILURE

What should I do now?
I am using the following windows xp iso file: Windows XP Pro SP2 2005 Gold Reloaded Edition.iso 
I have Hardy Heron 8.04 version of Ubuntu installed on my lap-top and I downloaded the VirtualBox 2.1.0 version for Linux Hosts from [www.virtualbox.org]("http://www.virtualbox.org")

Any help shall be greatly appreciated..

---

### Post by retskrad on 2008-12-28
Maybe try another? Or change the settings in "New".

---

### Post by zvacet on 2008-12-28
Did you add yourself to the vboxusers?

```
sudo adduser $USER vboxusers
```

---

### Post by john_galt on 2008-12-30
> **zvacet said:**
> Did you add yourself to the vboxusers?

```
sudo adduser $USER vboxusers
```

Yes, I have added myself.. and have tried to make new machines, but it's not working..
I will try making Windows Vista.. let's see if it works

---

