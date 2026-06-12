---
title: "Ubuntu Windows"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by blueliz5 on 2011-02-06
I'm trying to run Ubuntu alongside Windows and I do have the option to pick Ubuntu at startup, however I only get a carpet-looking screen with stripes once it does boot up. Normally I'm running windows vista..  Any suggestions?

---

### Post by 123456789123456789123456 on 2011-02-06
which is the main system?  windows or Ubuntu?

i'm assumeing that you had vista as the main system, and ubuntu as the second installation.  when doing this, vista is booting from the grub boot loader.  this may be causing problems with ubuntu.  solution.  you will need to use the live ubuntu cd to backup any data you have on the ubuntu installation.  use the vista cd to repair problems, it will install the vista boot loader in the MBR.  after that happens, ubuntu will no longer appear as an option, look for and download easyBCD.  then install ubuntu again, but this time, when it gets to the installing part, after the partitioning of the disk, choose advanced install method, tell the installer, not to install the GRUB boot loader on the MBR, but to use the ubuntu partition only.  after installation, go back to windows, since ubuntu partition will not appear.  run easyBCD.  that will allow you to choose Ubuntu as an option, and tell it that the GRUB is installed on that ubuntu partition, what will hapen is that easyBCD will edit the vista boot loaders files, to have Ubuntu as an option, and point it to that partition, after which point, Grub is located on that partition and the system starts to boot normally, note that the only problems I know of only accure with vista, so far, windows xp and 7 dont seem to have problems.

---

### Post by blueliz5 on 2011-02-11
Thanks I will try that!  I had the awful suspicion that vista would be what's causing this.

---

