---
title: "Samba errors"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by Papa-san on 2006-12-01
I am trying to get my Ubunto box to be able to print wirelessly to my wife's XP box. When I tried to install Samba, (sudo aptitude install samba) I got these messages:```
Installing new version of config file /etc/init.d/samba ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up libcrypt-smbhash-perl (0.12-1) ...
Setting up smbldap-tools (0.9.2-3) ...

Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
john@ubuntu:~$
```

I am trying to follow this 'how-to':
[http://ubuntuforums.org/showthread.php?t=32190&highlight=canon+i550](http://ubuntuforums.org/showthread.php?t=32190&highlight=canon+i550)
I am using the aptitude command because I need the dependency helps it offers, or I'll mess this install up, and everything seems to be working OK, for a change!

So, I beseech you networking wizards to impart some of your vast knowledge to this humble, recent linux convert!

Thanks! :rolleyes:

---

### Post by Papa-san on 2006-12-02
I have tried to fix this through synaptic, apt-get, and update manager. all of which result in the same errors...```
E: samba: subprocess post-installation script returned error exit status 102
E: samba-dbg: dependency problems - leaving unconfigured

```
I have attached a screenshot, for what it's worth...

---

### Post by Papa-san on 2006-12-03
I think this is the problem, but I have no idea as to a solution...
Evidently this is not able to find/ be found by whatever needs it, or whatever it needs...?  

HELP PLEASE?!?

```
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
```How do I link these?

---

### Post by odysseus.lost on 2006-12-15
See the following thread for the solution to this.
[http://ubuntuforums.org/showthread.php?t=240699&highlight=samba+error+102](http://ubuntuforums.org/showthread.php?t=240699&highlight=samba+error+102)

---

### Post by Papa-san on 2007-04-07
This worked as far as allowing the updater to work with samba...

Now, just seeking the courage to try configuring it!

---

