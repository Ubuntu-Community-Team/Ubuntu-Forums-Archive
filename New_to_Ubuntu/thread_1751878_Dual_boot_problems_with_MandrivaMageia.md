---
title: "Dual boot problems with Mandriva/Mageia"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by bennachie on 2011-05-07
While Kubuntu 11.04 is now my main distribution, I have also been testing the beta versions of Mageia. In attempting to have this as a subsidiary distribution in a multi-boot situation, I have run into a problem that I had previously experienced while attempting to use Mandriva in a similar way - the boot process terminates in a kernel panic because Grub2 doesn't properly identify the default boot location in Mageia/Mandriva. 

The problem doesn't seem to arise (for me, anyway) with other distributions still using Grub1, such as openSUSE and Fedora, and has apparently already been raised upstream. See:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=606904](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=606904)

This bug was marked as resolved in version 1.98 of Grub2 back in August 2010. Nevertheless, the issue still exists in version 1.99~rc1-13ubuntu, as used in Ubuntu and Kubuntu 11.04.

Is this a regression? Has anyone else experienced the same problem? Can anyone confirm that I should lodge a bug here, given the version number of the relevant package, rather than upstream?

---

