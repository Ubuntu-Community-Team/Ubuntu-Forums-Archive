---
title: "Ubuntu Software Center Error: Package Operation Failed"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by TheCreator on 2010-05-23
Hey Guys,
I'm a little bit of a "newbie" to Ubuntu. And, I just booted my laptop to the newest version. (10.04)

Well, I keep getting this error: Package Operation Failed

And, this is under the details:

```
nstallArchives() failed: Selecting previously deselected package libqt3-mt.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 130613 files and directories currently installed.)
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8-b-6ubuntu2_i386.deb) ...
Selecting previously deselected package libavahi-qt3-1.
Unpacking libavahi-qt3-1 (from .../libavahi-qt3-1_0.6.25-1ubuntu6_i386.deb) ...
Selecting previously deselected package liblua50.
Unpacking liblua50 (from .../liblua50_5.0.3-4_i386.deb) ...
Selecting previously deselected package liblualib50.
Unpacking liblualib50 (from .../liblualib50_5.0.3-4_i386.deb) ...
Selecting previously deselected package kdelibs-data.
Unpacking kdelibs-data (from .../kdelibs-data_4%3a3.5.10.dfsg.1-3ubuntu2_all.deb) ...
Selecting previously deselected package kdelibs4c2a.
Unpacking kdelibs4c2a (from .../kdelibs4c2a_4%3a3.5.10.dfsg.1-3ubuntu2_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.1.41-3ubuntu12.1_all.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.41-3ubuntu12.1_i386.deb) ...
Selecting previously deselected package librecode0.
Unpacking librecode0 (from .../librecode0_3.6-17_i386.deb) ...
Selecting previously deselected package libxerces-c28.
Unpacking libxerces-c28 (from .../libxerces-c28_2.8.0+deb1-2build1_i386.deb) ...
Selecting previously deselected package libxalan110.
Unpacking libxalan110 (from .../libxalan110_1.10-4_i386.deb) ...
Selecting previously deselected package docbook-xsl.
Unpacking docbook-xsl (from .../docbook-xsl_1.75.2+dfsg-3_all.deb) ...
Selecting previously deselected package anymeal.
Unpacking anymeal (from .../anymeal_0.30-8ubuntu2_i386.deb) ...
Selecting previously deselected package docbook-xsl-doc-html.
Unpacking docbook-xsl-doc-html (from .../docbook-xsl-doc-html_1.75.2-1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 26 changed 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
Setting up libclucene0ldbl (0.9.21b-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libclucene0ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libexiv2-6 (0.19-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libexiv2-6 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libiodbc2 (3.52.6-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libiodbc2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-sql (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-sql (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-sql (= 4:4.6.2-0ubuntu5); however:
  Package libqt4-sql is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-svg (4:4.6.2-0ubuntu5) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-svg (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-xmlpatterns (4:4.6.2-0ubuntu5) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-xmlpatterns (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqt4-webkit:
 libqt4-webkit depends on libqt4-xmlpatterns (= 4:4.6.2-0ubuntu5); however:
  Package libqt4-xmlpatterns is not configured yet.
dpkg: error processing libqt4-webkit (--configure):
 dependency problems - leaving unconfigured
Setting up libstreams0 (0.7.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libstreams0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libstreamanalyzer0:
 libstreamanalyzer0 depends on libclucene0ldbl (>= 0.9.21b); however:
  Package libclucene0ldbl is not configured yet.
 libstreamanalyzer0 depends on libexiv2-6; however:
  Package libexiv2-6 is not configured yet.
 libstreamanalyzer0 depends on libstreams0 (= 0.7.2-0ubuntu1); however:
  Package libstreams0 is not configured yet.
dpkg: error processing libstreamanalyzer0 (--configure):
 dependency problems - leaving unconfigured
Setting up libpolkit-qt-1-0 (0.95.1-1fakesync1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpolkit-qt-1-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of soprano-daemon:
 soprano-daemon depends on libiodbc2 (>= 3.52.6); however:
  Package libiodbc2 is not configured yet.
dpkg: error processing soprano-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsoprano4:
 libsoprano4 depends on libclucene0ldbl (>= 0.9.21b); however:
  Package libclucene0ldbl is not configured yet.
 libsoprano4 depends on soprano-daemon (= 2.4.2+dfsg.1-0ubuntu1.1); however:
  Package soprano-daemon is not configured yet.
dpkg: error processing libsoprano4 (--configure):
 dependency problems - leaving unconfigured
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already

Setting up libavahi-qt3-1 (0.6.25-1ubuntu6) ...

Setting up liblua50 (5.0.3-4) ...

Setting up liblualib50 (5.0.3-4) ...

Setting up kdelibs-data (4:3.5.10.dfsg.1-3ubuntu2) ...

Setting up kdelibs4c2a (4:3.5.10.dfsg.1-3ubuntu2) ...

Setting up mysql-common (5.1.41-3ubuntu12.1) ...
Setting up libmysqlclient16 (5.1.41-3ubuntu12.1) ...

Setting up librecode0 (3.6-17) ...

Setting up libxerces-c28 (2.8.0+deb1-2build1) ...

Setting up libxalan110 (1.10-4) ...

Setting up docbook-xsl (1.75.2+dfsg-3) ...

Setting up anymeal (0.30-8ubuntu2) ...

Setting up docbook-xsl-doc-html (1.75.2-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libclucene0ldbl
 libexiv2-6
 libiodbc2
 libqt4-sql
 libqt4-qt3support
 libqt4-svg
 libqt4-xmlpatterns
 libqt4-webkit
 libstreams0
 libstreamanalyzer0
 libpolkit-qt-1-0
 soprano-daemon
 libsoprano4
Setting up libiodbc2 (3.52.6-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libiodbc2 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of soprano-daemon:
 soprano-daemon depends on libiodbc2 (>= 3.52.6); however:
  Package libiodbc2 is not configured yet.
dpkg: error processing soprano-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-sql (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-sql (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libstreams0 (0.7.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libstreams0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-svg (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-svg (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsoprano4:
 libsoprano4 depends on soprano-daemon (= 2.4.2+dfsg.1-0ubuntu1.1); however:
  Package soprano-daemon is not configured yet.
dpkg: error processing libsoprano4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstreamanalyzer0:
 libstreamanalyzer0 depends on libstreams0 (= 0.7.2-0ubuntu1); however:
  Package libstreams0 is not configured yet.
dpkg: error processing libstreamanalyzer0 (--configure):
 dependency problems - leaving unconfigured
Setting up libexiv2-6 (0.19-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libexiv2-6 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-sql (= 4:4.6.2-0ubuntu5); however:
  Package libqt4-sql is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
Setting up libclucene0ldbl (0.9.21b-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libclucene0ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-xmlpatterns (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-xmlpatterns (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpolkit-qt-1-0 (0.95.1-1fakesync1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpolkit-qt-1-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqt4-webkit:
 libqt4-webkit depends on libqt4-xmlpatterns (= 4:4.6.2-0ubuntu5); however:
  Package libqt4-xmlpatterns is not configured yet.
dpkg: error processing libqt4-webkit (--configure):
 dependency problems - leaving unconfigured
```

I get this on everything I try to download from Ubuntu Software Center. It wasn't like this earlier, and just begun doing this about an hour ago. So, If anyone could help it would be greatly appreciated!!:guitar:

---

### Post by hryanjones on 2010-05-28
Try using Synaptic Package Manager (you can find it in
System > Administration > Synaptic

Especially look under Edit Menu > Fix Broken Packages

---

### Post by bluelaguna on 2010-06-02
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

---

