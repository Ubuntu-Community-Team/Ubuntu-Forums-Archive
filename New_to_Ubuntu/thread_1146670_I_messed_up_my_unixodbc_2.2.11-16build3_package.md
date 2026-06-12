---
title: "I messed up my unixodbc 2.2.11-16build3 package"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by k6mkf on 2009-05-02
Hi Team,

Installing packages, I keep getting this error:

(Readinew@bugs.launchpad.netng database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `odbcinst1debian1' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

So I looked at odbcinst1debian1.list:

mike@mike-ubuntu7:/var/lib/dpkg/info$ more odbcinst1debian1.list
ard, Winbook Model XP5, Yahoo! Internet Keyboard

Name: console-setup/modelcode
Template: console-setup/modelcode
Value: pc105
Owners: console-setup

Name: console-setup/optionscode
Template: console-setup/optionscode
Value: 
Owners: console-setup

Name: console-setup/switch
Template: console-setup/switch
Value: No temporary switch
Owners: console-setup

Name: console-setup/toggle
Template: console-setup/toggle
Value: No toggling
Owners: console-setup

Name: console-setup/ttys
Template: console-setup/ttys
Value: /dev/tty[1-6]
Owners: console-setup

Name: console-setup/variant
Template: console-setup/variant
Value: USA
Owners: console-setup
Flags: seen
Variables:
 CHOICES = USA, USA - Alternative international (former us_intl), USA - Cherokee
, USA - Classic Dvorak, USA - Colemak, USA - Dvorak, USA - Dvorak international,
 USA - Group toggle on multiply/divide key, USA - International (AltGr dead 
mike@mike-ubuntu7:/var/lib/dpkg/info$ 

That certainly doesn't look like the other .list files here, that look like this:

mike@mike-ubuntu7:/var/lib/dpkg/info$ more gdm.list
/.
/var
/var/log
/var/log/gdm
/var/lib
/var/lib/gdm
/usr
/usr/share
/usr/share/faces
/usr/share/hosts
/usr/share/pixmaps
/usr/share/pixmaps/gdm.xpm
/usr/share/pixmaps/gdmDebianLogo.xpm
/usr/share/pixmaps/login-photo.xpm
/usr/share/pixmaps/gdm-foot-logo.png
/usr/share/pixmaps/nobody.png
/usr/share/pixmaps/nohost.png
/usr/share/pixmaps/faces
/usr/share/pixmaps/faces/astronaut.jpg
/usr/share/pixmaps/faces/baseball.png
/usr/share/pixmaps/faces/butterfly.png
/usr/share/pixmaps/faces/cat-eye.jpg
/usr/share/pixmaps/faces/chess.jpg
unixodbc

So I reinstalled the unixodbc 2.2.11-16build3 package using the package manager, but the odbcinst1debian1.list file remains the same.

What do I need to get the correct contents for the odbcinst1debian1.list file?  Thanks for your help !!! :confused:

---

### Post by k6mkf on 2009-05-03
OK, so I found the contents of odbcinst1debian1.list online, so updated it as follows:

mike@mike-ubuntu9:/var/lib/dpkg/info$ cat odbcinst1debian1.list
/.
/etc
/etc/ODBCDataSources
/etc/odbc.ini
/etc/odbcinst.ini
/usr
/usr/lib
/usr/lib/libodbcinst.so.1.0.0
/usr/lib/odbc
/usr/lib/odbc/libesoobS.so
/usr/lib/odbc/libmimerS.so
/usr/lib/odbc/libodbcdrvcfg1S.so
/usr/lib/odbc/libodbcdrvcfg2S.so
/usr/lib/odbc/libodbcminiS.so
/usr/lib/odbc/libodbcmyS.so
/usr/lib/odbc/libodbcnnS.so
/usr/lib/odbc/libodbcpsqlS.so
/usr/lib/odbc/libodbctxtS.so
/usr/lib/odbc/liboplodbcS.so
/usr/lib/odbc/liboraodbcS.so
/usr/lib/odbc/libsapdbS.so
/usr/lib/odbc/libtdsS.so
/usr/bin
/usr/bin/odbcinst
/usr/share
/usr/share/doc
/usr/share/doc/odbcinst1debian1
/usr/share/doc/odbcinst1debian1/copyright
/usr/share/doc/odbcinst1debian1/changelog.gz
/usr/share/doc/odbcinst1debian1/changelog.Debian.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/odbcinst1debian1
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/odbcinst.1.gz
/usr/lib/libodbcinst.so.1
mike@mike-ubuntu9:/var/lib/dpkg/info$ 

My problems now seem to be all around this:

Setting up unixodbc (2.2.11-16build3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing unixodbc (--configure):
subprocess post-installation script returned error exit status 2

This is the consistent failure mode.

---

### Post by k6mkf on 2009-05-03
I finally removed postfix, java and unixodbc completely, then installed unixodbc.  unixodbc installed correctly, so I'll reinstall java later.  :P

---

