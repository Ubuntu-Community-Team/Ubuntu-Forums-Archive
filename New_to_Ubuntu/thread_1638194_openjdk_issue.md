---
title: "openjdk issue"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ex_isp on 2010-12-05
Greetings.

Trying to install openjdk into an ISO file.  Ran command "apt-get install openjdk-6-jre".
Tried again this morn and got output of

openjdk-6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  make
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 90 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up ca-certificates-java (20100412) ...
the keytool command requires a mounted proc fs (/proc).
dpkg: error processing ca-certificates-java (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-6-jre-headless (6b18-1.8.2-4) ...
the java command requires a mounted proc fs (/proc).
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8.2-4); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jdk:
 openjdk-6-jdk depends on openjdk-6-jre (>= 6b18-1.8.2-4); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing openjdk-6-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8.2-4); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ca-certificates-java
 openjdk-6-jre-headless
 openjdk-6-jre
 openjdk-6-jdk
 icedtea-6-jre-cacao
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I solve this?

Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ca-certificates-java
 openjdk-6-jre-headless
 openjdk-6-jre
 openjdk-6-jdk
 icedtea-6-jre-cacao
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help?

Thanks much!

---

### Post by ex_isp on 2010-12-05
Bump

---

### Post by ex_isp on 2010-12-05
bump again

---

### Post by meteormatt on 2011-07-18
> **ex_isp said:**
> Greetings.

Trying to install openjdk into an ISO file.  Ran command "apt-get install openjdk-6-jre".
Tried again this morn and got output of

openjdk-6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  make
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 90 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up ca-certificates-java (20100412) ...
the keytool command requires a mounted proc fs (/proc).
dpkg: error processing ca-certificates-java (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-6-jre-headless (6b18-1.8.2-4) ...
the java command requires a mounted proc fs (/proc).
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8.2-4); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jdk:
 openjdk-6-jdk depends on openjdk-6-jre (>= 6b18-1.8.2-4); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing openjdk-6-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8.2-4); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ca-certificates-java
 openjdk-6-jre-headless
 openjdk-6-jre
 openjdk-6-jdk
 icedtea-6-jre-cacao
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I solve this?

Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ca-certificates-java
 openjdk-6-jre-headless
 openjdk-6-jre
 openjdk-6-jdk
 icedtea-6-jre-cacao
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help?

Thanks much!
I face the same problem today.

---

