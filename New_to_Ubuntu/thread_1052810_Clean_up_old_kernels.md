---
title: "Clean up old kernels"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by pzs on 2009-01-28
Is there a standard way to do this? If you update whenever new releases become available, eventually the /boot partition fills up with old kernels you're not using. At the moment, I use 

```

dpkg -l | grep linux

```

to locate the package names for old kernels and apt-get remove to remove them. Is there a better way?

---

### Post by bumanie on 2009-01-28
That's probably as good way as there is. Most people just comment them out in /boot/grub/menu.lst, but as you have a /boot partition, you don't have the choice of leaving them there (unless you have a large /bot of course). What you are doing, seems as easy as any other way.

---

### Post by RichardLinx on 2009-01-28
> **pzs said:**
> Is there a better way?

Yes, there is. Run this command:

```
sudo apt-get autoremove
```
This will remove all old kernels and packages.

I usually run this after installing a large number of updates or a kernel update. Afterwards I run:

```
sudo apt-get autoclean
```

---

### Post by drs305 on 2009-01-28
Here is a link to a tutorial I wrote about StartUp-Manager - a gui app that can tweak grub's menu without having to manually edit it. You can limit the number of kernels displayed, menu timeout, default OS or kernel, and much more.

It also discusses how to remove kernels or merely stop displaying them on the menu (but continuing to retain them on the system).

[URL="http://ubuntuforums.org/showthread.php?t=818177"] HOWTO: Grub Menu Kernel Display Options
[/URL]

---

