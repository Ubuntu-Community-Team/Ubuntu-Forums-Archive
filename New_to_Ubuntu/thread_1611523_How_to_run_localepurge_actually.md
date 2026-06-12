---
title: "How to run localepurge actually?"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by allencch on 2010-11-02
Hello, I am using Ubuntu 10.10. I installed localepurge, and tried to run it.
I used "sudo dpkg-recofigure localepurge" and generated the /etc/locale.nopurge file as following:

```

####################################################
# This is the configuration file for localepurge(8).
####################################################

####################################################
# Uncommenting this string enables removal of localized 
# man pages based on the configuration information for
# locale files defined below:

MANDELETE

####################################################
# Uncommenting this string causes localepurge to simply delete
# locales which have newly appeared on the system without
# bothering you about it:

DONTBOTHERNEWLOCALE

####################################################
# Uncommenting this string enables display of freed disk
# space if localepurge has purged any superfluous data:

SHOWFREEDSPACE

#####################################################
# Commenting out this string enables faster but less
# accurate calculation of freed disk space:

QUICKNDIRTYCALC

#####################################################
# Commenting out this string disables verbose output:

#VERBOSE

#####################################################
# Following locales won't be deleted from this system
# after package installations done with apt-get(8):

DONTBOTHERNEWLOCALE
en
MANDELETE
NEEDSCONFIGFIRST
SHOWFREEDSPACE
zh

```

But after that, I run "sudo localepurge", it asked me to use "sudo dpkg-reconfigure localepurge" again. Is there anything wrong for my configuration step? I have tried a lot of times, still cannot purge the files.

---

### Post by oldos2er on 2010-11-02
How did you install localepurge? Usually you configure it during its installation, and afterward it runs automatically after installing a package.

---

### Post by allencch on 2010-11-02
> **oldos2er said:**
> How did you install localepurge? Usually you configure it during its installation, and afterward it runs automatically after installing a package.
I forgot the way I installed. Might using "Synaptic Package Manager".

---

### Post by allencch on 2010-11-03
I have managed to solve the problem by remove it, and reinstall using commandline:
```
sudo apt-get install localepurge
```
By this way, I will go to the configuration page after installation. If using Synaptic Package Manager, there is no configuration page.

---

