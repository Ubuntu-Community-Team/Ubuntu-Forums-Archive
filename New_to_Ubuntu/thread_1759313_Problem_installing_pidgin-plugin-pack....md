---
title: "Problem installing pidgin-plugin-pack..."
date: 2011-05-15
forum: New to Ubuntu
---

### Post by UUUnicorn on 2011-05-15
Hello again.

Please, I encountered a problem when I tried installing pidgin-plugin-pack through Software Manager in Xubuntu. The following is what I saw onscreen:

installArchives() failed: Selecting previously deselected package pidgin-plugin-pack.
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
(Reading database ... 174634 files and directories currently installed.)
Unpacking pidgin-plugin-pack (from .../pidgin-plugin-pack_2.6.3-2_i386.deb) ...
Setting up amavisd-new-postfix (1:2.6.5-0ubuntu2) ...

Postfix not configured. Run
sudo dpkg-reconfigure postfix and choose
the type of mail server. Then run
sudo dpkg-reconfigure amavisd-new-postfix to
finish amavisd-new-postfix installation.

Stopping amavisd: (not running).
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "elizabethanne-U90-U100", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "restart" failed.
dpkg: error processing amavisd-new-postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up pidgin-plugin-pack (2.6.3-2) ...
Errors were encountered while processing:
 amavisd-new-postfix
Setting up amavisd-new-postfix (1:2.6.5-0ubuntu2) ...

Postfix not configured. Run
sudo dpkg-reconfigure postfix and choose
the type of mail server. Then run
sudo dpkg-reconfigure amavisd-new-postfix to
finish amavisd-new-postfix installation.

Stopping amavisd: (not running).
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "elizabethanne-U90-U100", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "restart" failed.
dpkg: error processing amavisd-new-postfix (--configure):
 subprocess installed post-installation script returned error exit status 1

It looks like it has to do with e-mail. When I tried what it suggested, I got a screen that wouldn't allow me to select anything. I still got a white check mark in a green circle, indicating that pidgin-plugin-pack did get installed.

Thank you very much for your advice/help.

Sincerely,

UUUnicorn

---

### Post by UUUnicorn on 2011-05-16
I solved this problem by going into Synaptic Package Manager, searching for "amavisd", and uninstalling amavisd and everything amavisd-related.

Please, I'm wondering, however, if I should reinstall these. I do know that they have to do with ClamAV/ClamTk, but are these really necessary?  :confused:

Thank you.

Sincerely,

UUUnicorn (Born confused--sorry!)

---

