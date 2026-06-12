---
title: "SELinux and Ubuntu....good Idea?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-01-21
I was thinking about installing SELinux on my ubuntu desktop for the pure purpose of study and evaluation. I know that SELinux comes standard with other distros but notice when I searched for it in the Synaptic Package Manager that Canonical does not support SELinux. What are the potential consequences to adding this to my Ubuntu system, if any? Is there something comparable?

---

### Post by Rubi1200 on 2011-01-21
From what I have read, support for SELinux on Ubuntu is not that great.

You would be better off trying Fedora. It even has a SELinux Troubleshooter application.

---

### Post by ubudog on 2011-01-21
> **Rubi1200 said:**
> From what I have read, support for SELinux on Ubuntu is not that great.

You would be better off trying Fedora. It even has a SELinux Troubleshooter application.

Agreed.  Fedora supports it much better than Ubuntu.  In all these years, I don't think I've ever seen SELinux run on Ubuntu... but then again, it's possible.  

[https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)

---

### Post by HermanAB on 2011-01-21
Well, you will sure learn a lot if you try it on Ubuntu, since the moment you enable it, nothing will work anymore...

There are various MAC systems: Tomoyo, SELinux and AppArmour are the best known, and they all address the problem in more or less the same way.

---

### Post by NightwishFan on 2011-01-21
Apparmor is similar and supported by Canonical. [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

SELinux is possible though I have never tried it myself. I usually (like now) recommend the above.

---

### Post by ubudog on 2011-01-21
> **HermanAB said:**
> Well, you will sure learn a lot if you try it on Ubuntu, since the moment you enable it, nothing will work anymore...

There are various MAC systems: Tomoyo, SELinux and AppArmour are the best known, and they all address the problem in more or less the same way.

Hmm...

---

### Post by ubudog on 2011-01-21
> **NightwishFan said:**
> Apparmor is similar and supported by Canonical. [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

SELinux is possible though I have never tried it myself. I usually (like now) recommend the above.

Yes, Apparmor is awesome.

---

### Post by Rubi1200 on 2011-01-21
If you want to understand (and possibly implement) AppArmor, read the sticky by bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by bodhi.zazen on 2011-01-21
> **Nickjpost said:**
> I was thinking about installing SELinux on my ubuntu desktop for the pure purpose of study and evaluation. I know that SELinux comes standard with other distros but notice when I searched for it in the Synaptic Package Manager that Canonical does not support SELinux. What are the potential consequences to adding this to my Ubuntu system, if any? Is there something comparable?

It is possible to do selinux on ubuntu, but it is far easier to use Fedora if you want selinux.

Fedora has a number of tools, both graphical and command line, that are lacking in the Ubuntu repositories, the selinux policies are more refined, and you will get better support (for selinux) on the Fedora forums then here.

Some people use selinux here (/me wonders who), but far fewer then Fedora.

---

### Post by ubudog on 2011-01-21
> **bodhi.zazen said:**
> It is possible to do selinux on ubuntu, but it is far easier to use Fedora if you want selinux.

Fedora has a number of tools, both graphical and command line, that are lacking in the Ubuntu repositories, the selinux policies are more refined, and you will get better support (for selinux) on the Fedora forums then here.

Some people use selinux here (/me wonders who), but far fewer then Fedora.

Totally agree.  Fedora has SELinux very, very integrated into it's system.

---

