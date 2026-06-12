---
title: "lighttpd - anyone installed it successfully on 64bit"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by kylea on 2009-11-09
I am trying to install lighttpd on 64bit Karmic and I am getting an error that I cannot sort out.

Has anyone got it working / installed successfully.

Here is the Install log

-----------------------------------------------------------------------

Selecting previously deselected package lighttpd.
(Reading database ... 421795 files and directories currently installed.)
Unpacking lighttpd (from .../lighttpd_1.4.22-1ubuntu4_amd64.deb) ...
Selecting previously deselected package lighttpd-doc.
Unpacking lighttpd-doc (from .../lighttpd-doc_1.4.22-1ubuntu4_all.deb) ...
Selecting previously deselected package lighttpd-mod-magnet.
Unpacking lighttpd-mod-magnet (from .../lighttpd-mod-magnet_1.4.22-1ubuntu4_amd64.deb) ...
Selecting previously deselected package mono-fastcgi-server2.
Unpacking mono-fastcgi-server2 (from .../mono-fastcgi-server2_2.4.2-1_all.deb) ...
Selecting previously deselected package mono-fastcgi-server.
Unpacking mono-fastcgi-server (from .../mono-fastcgi-server_2.4.2-1_all.deb) ...
Processing triggers for ufw ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...

Setting up spawn-fcgi (1.6.3-0.1~ppa1~karmic1) ...

update-alternatives: error: alternative path /usr/bin/spawn-fcgi.standalone doesn't exist.

dpkg: error processing spawn-fcgi (--configure):
 subprocess installed post-installation script returned error exit status 2

Setting up lighttpd (1.4.22-1ubuntu4) ...
Installing new version of config file /etc/init.d/lighttpd ...
Installing new version of config file /etc/logrotate.d/lighttpd ...
update-alternatives: using /usr/bin/spawn-fcgi.lighttpd to provide /usr/bin/spawn-fcgi (spawn-fcgi) in auto mode.
update-alternatives: warning: not replacing /usr/bin/spawn-fcgi with a link.
update-alternatives: warning: not replacing /usr/share/man/man1/spawn-fcgi.1.gz with a link.
Syntax OK

* Starting web server lighttpd
   ...done.

Setting up lighttpd-doc (1.4.22-1ubuntu4) ...
Setting up lighttpd-mod-magnet (1.4.22-1ubuntu4) ...
Setting up mono-fastcgi-server2 (2.4.2-1) ...
Setting up mono-fastcgi-server (2.4.2-1) ...

Errors were encountered while processing: spawn-fcgi
E: Sub-process /usr/bin/dpkg returned an error code (1)

A package failed to install.  Trying to recover:

Setting up spawn-fcgi (1.6.3-0.1~ppa1~karmic1) ...
update-alternatives: error: alternative path /usr/bin/spawn-fcgi.standalone doesn't exist.

dpkg: error processing spawn-fcgi (--configure):
 subprocess installed post-installation script returned error exit status 2

Errors were encountered while processing: spawn-fcgi

---

### Post by kylea on 2009-11-09
Update - I downgraded spawn-fcgi to version 1.6.2-2 - I assume that will be ok.

I re-installed lighttpd and it installed with out complaint.

---

