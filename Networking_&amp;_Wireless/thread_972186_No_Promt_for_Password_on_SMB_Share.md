---
title: "No Promt for Password on SMB Share"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by pkkid on 2008-11-05
I am trying to setup an SMB share.  One directory with a password, and logged in as if I am my user mjs721.  The other directory just shared everything as read only.

I read all the help pages and at least 5 other pages and they all say the same thing.  Use some form of smb.conf like the one shown below. run smbpasswd to create the user account in smb land.

The result.  My public share works as expected.  My private share just says permission denied, but does not prompt me to log in.

I'm running Ubuntu 8.10 Upgraded from 8.04
Testing SMB Share from VirtualBox on the same machine running WinXP.

Anyone know whats going on?


```
#
# My Samba Configuration
#
# TO TEST SETTINGS: >> testparm smb.conf
# TO RELOAD RUN:    >> sudo /etc/init.d/samba reload
#

#======================= Global Settings =======================

[global]
  # Browsing/Identification #
  workgroup = MSHOME
  netbios name = pkkid-ubuntu
  server string = %h server

  # Authentication #
  security = user
  smb passwd file = /etc/samba/smbpasswd
  passwd program = /usr/bin/passwd %u
  unix password sync = Yes
  encrypt passwords = true
  map to guest = bad user
  guest account = nobody
  passdb backend = smbpasswd
  obey pam restrictions = yes
  invalid users = root

  # Debugging/Accounting #
  log file = /var/log/samba/log.%m
  max log size = 1000
  syslog = 0

  # Defaults #
  browseable = yes
  read only = yes
  writeable = no
  create mask = 0555
  directory mask = 0755


#======================= Share Definitions =======================

[Drobo]
  comment = Private Share
  path = /media/Drobo
  read only = no
  writeable = yes
  valid users = mjs7231


[Shared]
  comment = Public Share
  path = /media/Drobo/Shared
  guest only = yes
  guest ok = yes



```

---

### Post by pkkid on 2008-11-05
No Samba guys here? :(

---

