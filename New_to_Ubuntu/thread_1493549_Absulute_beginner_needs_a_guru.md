---
title: "Absulute beginner needs a guru"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by bobmac on 2010-05-26
Folks,

It would appear that I've managed to make a hash of upgrading from 8.04 LTS to 10.4 LTS. To upgrade I used Alt+F2, and at the dialog entered 'upgrade-manager --devel-release' as described under [http://www.ubuntu.com.getubuntu/upgrading](http://www.ubuntu.com.getubuntu/upgrading) under the heading Upgrade from 8.04 LTS to 10.04 LTS Network Upgrade for Ubuntu Desktops (Recommended). The upgrade appeared to work OK.

During installation, on several occasions I was requested to either leave the menu.lst file as is or to select from several options. As the default was to leave it alone this is what I selected.

However, when I start up my system it still shows the 8.04 stuff.

I suspect that I should have selected on of the several options that were available but WHICH ONE?

As it is, how do I fix this. Or do I have to reinstall the upgrade again, and if so how do I go about it.

Regards,

Bob

---

### Post by hacker918 on 2010-05-26
> **bobmac said:**
> Folks,

It would appear that I've managed to make a hash of upgrading from 8.04 LTS to 10.4 LTS. To upgrade I used Alt+F2, and at the dialog entered 'upgrade-manager --devel-release' as described under [http://www.ubuntu.com.getubuntu/upgrading](http://www.ubuntu.com.getubuntu/upgrading) under the heading Upgrade from 8.04 LTS to 10.04 LTS Network Upgrade for Ubuntu Desktops (Recommended). The upgrade appeared to work OK.

During installation, on several occasions I was requested to either leave the menu.lst file as is or to select from several options. As the default was to leave it alone this is what I selected.

However, when I start up my system it still shows the 8.04 stuff.

I suspect that I should have selected on of the several options that were available but WHICH ONE?

As it is, how do I fix this. Or do I have to reinstall the upgrade again, and if so how do I go about it.

Regards,

Bob
While I'm certainly no "guru," I would say that you would attract attention from the right people if you would choose more descriptive titles.

---

### Post by exodus_ on 2010-05-26
hey there,

Since you upgraded its entirely possible that your old kernel was left there as a fallback option in case something breaks.  This can be a good thing since it prevents your system from being left in a state where it will not boot.

```
ls /boot
```  in a terminal will show you what kernels are installed currently.

If you REALLY don't want the old kernels showing up in your grub menu there are a number of ways you could "fix" this.

using your favourite package tool (apt-get, aptitude, synaptic, etc) you could remove the old kernels and then ```
sudo update-grub
``` in a terminal will update your grub config and remove the old entries.

It's probably best though to have at least one previous kernel laying around for troubleshooting if something DOES break though

---

### Post by 311005901 on 2010-05-26
I'm no guru, but I'm guessing you're talking about the actual application menu, correct?

---

### Post by 3rdalbum on 2010-05-26
> **bobmac said:**
> 
During installation, on several occasions I was requested to either leave the menu.lst file as is or to select from several options. As the default was to leave it alone this is what I selected.

However, when I start up my system it still shows the 8.04 stuff.

It would - leaving the menu.lst as it is means that the menu doesn't contain any 10.04 kernel entries.

Running:

```
sudo update-grub
```

in the terminal should fix this.

---

### Post by bobmac on 2010-05-26
Many thanks for all who replied with the information to fix my problem which has worked. As an aside, when I upgrade again do you happen to know which option I should choose when the menu.lst messages display. As I mentioned, this time around I simply chose the default which if I recall correctly, is to lease the menu.lst as is.

Regards,

Bob

---

