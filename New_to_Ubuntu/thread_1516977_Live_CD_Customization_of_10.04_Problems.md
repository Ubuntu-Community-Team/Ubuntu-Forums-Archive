---
title: "Live CD Customization of 10.04 Problems"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-06-24
Ok, so I used apt-mirror to make a repository of the current packages that ubuntu 10.04 sources.list offer and added into my webserver.

A few problems arose as you can imagine since I am used to doing 8.04.2 Live cd customization and I pretty much took my script and the sources.list and just added lucid instead of hardy.

Are the lucid-backports up?

Also which repository do I use for the medibuntu addresses, as it seems like they are not online, I didnt add medibuntu to my personal repository due to the keyring and stuff.

```
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-base depends on libhsqldb-java (>> 1.8.0.10); however:
  Package libhsqldb-java is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on default-jre | gcj-jre | java-gcj-compat (>= 1.0.77-4) | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-officebean depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 openjdk-6-jre-headless
 libservlet2.5-java
 libhsqldb-java
 openjdk-6-jre
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org-report-builder-bin
 openoffice.org-officebean
 openoffice.org-filter-mobiledev
 openoffice.org
 icedtea-6-jre-cacao
 icedtea6-plugin
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up openjdk-6-jre-headless (6b18-1.8-0ubuntu1) ...
the java command requires a mounted proc fs (/proc).
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.5-java:
 libservlet2.5-java depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however:
  Package default-jre-headless is not installed.
  Package java2-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet.
  Package java5-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing libservlet2.5-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on default-jre | gcj-jre | java-gcj-compat (>= 1.0.77-4) | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-officebean depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-base depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on default-jre-headless | java2-runtime-headless; however:
  Package default-jre-headless is not installed.
  Package java2-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet.
 libhsqldb-java depends on libservlet2.5-java; however:
  Package libservlet2.5-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 libservlet2.5-java
 openoffice.org-java-common
 openoffice.org-officebean
 openoffice.org-base
 icedtea6-plugin
 libhsqldb-java
 openoffice.org-filter-mobiledev
 ca-certificates-java
 openoffice.org-report-builder-bin
 openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


Installing Flash plugin for Firefox... Done

cp: cannot stat `ubuntu-wallpapers.xml': No such file or directory
update-rc.d: warning: /etc/init.d/upcstartup missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/upcstartup ...
   /etc/rc1.d/K99upcstartup -> ../init.d/upcstartup
   /etc/rc2.d/S99upcstartup -> ../init.d/upcstartup
   /etc/rc3.d/S99upcstartup -> ../init.d/upcstartup
   /etc/rc4.d/S99upcstartup -> ../init.d/upcstartup
   /etc/rc5.d/S99upcstartup -> ../init.d/upcstartup

```

The above is some of the problems, and here is some more

```
Setting up openjdk-6-jre-headless (6b18-1.8-0ubuntu1) ...
the java command requires a mounted proc fs (/proc).
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.5-java:
 libservlet2.5-java depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however:
  Package default-jre-headless is not installed.
  Package java2-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet.
  Package java5-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing libservlet2.5-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on default-jre | gcj-jre | java-gcj-compat (>= 1.0.77-4) | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-officebean depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-base depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhsqldb-java:
 libhsqldb-java depends on default-jre-headless | java2-runtime-headless; however:
  Package default-jre-headless is not installed.
  Package java2-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet.
 libhsqldb-java depends on libservlet2.5-java; however:
  Package libservlet2.5-java is not configured yet.
dpkg: error processing libhsqldb-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however:
  Package default-jre is not installed.
  Package gcj-jre is not installed.
  Package java-gcj-compat is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java5-jre is not installed.
  Package sun-java6-jre is not installed.
  Package java5-runtime is not installed.
  Package openjdk-6-jre which provides java5-runtime is not configured yet.
  Package jre is not installed.
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>= 1:3.2.0~); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 libservlet2.5-java
 openoffice.org-java-common
 openoffice.org-officebean
 openoffice.org-base
 icedtea6-plugin
 libhsqldb-java
 openoffice.org-filter-mobiledev
 ca-certificates-java
 openoffice.org-report-builder-bin
 openoffice.org
Err http://packages.medibuntu.org lucid Release.gpg
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org/ lucid/free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org/ lucid/non-free Translation-en_US
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign http://packages.medibuntu.org lucid Release
Ign http://packages.medibuntu.org lucid/free Packages
Ign http://packages.medibuntu.org lucid/non-free Packages
Ign http://packages.medibuntu.org lucid/free Packages
Ign http://packages.medibuntu.org lucid/non-free Packages
Err http://packages.medibuntu.org lucid/free Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org lucid/non-free Packages
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Now what I can gather is that open office and the java are associated with either lucid backports or medibuntu, and that is why they are failing to install I guess.

Also I have the Missing LSB information Error in my startup script.
I am guessing this is not really a big deal?

Well thats it for now, im sure more problems will arise, anyone know about these repositories and openoffice/java files that are failing and perhaps the missing LSB information?

---

### Post by ericeclifford on 2010-06-24
I guess what I will do is just try the sources.list that came with the install of it.

Instead of my repository, it could of got messed up, but I highly doubt it.

---

