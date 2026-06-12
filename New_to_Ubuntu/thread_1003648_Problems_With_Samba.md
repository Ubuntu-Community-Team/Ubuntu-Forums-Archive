---
title: "Problems With Samba"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by john.hall on 2008-12-06
I'm trying to remove samba AND it's configuration files.  However,
```

apt-get remove samba

```
Doesn't remove them, and 
```

apt-get --purge remove samba

```
doesn't remove the files in /etc/samba.

I removed them manually, and now I complains when I try to reinstall samba (probably because it doesn't create new configuration files):
```

root@joha-desktop:/etc# apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4369kB of archives.
After this operation, 12.2MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 130907 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.2.3-1ubuntu3.3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up samba (2:3.2.3-1ubuntu3.3) ...
Generating /etc/default/samba...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Does anybody have any ideas?  Thanks.

---

### Post by zwaardmeester on 2008-12-06
```

sudo cp /usr/share/samba/smb.conf /etc/samba/
sudo apt-get install samba

```
should do the job. This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/254151").

You also might want to put
```
   encrypt passwords = true
```
one line 103. This is namely the only different line between my 'ubuntu' smb.conf an the default one.

---

### Post by john.hall on 2008-12-06
OK, now that Samba is installed and I don't have anything strange in my smb.conf, how do I set up passwordless access?

I followed the steps here: [http://ubuntuforums.org/showthread.php?t=658056](http://ubuntuforums.org/showthread.php?t=658056)
but Windows still asks for a password.

---

### Post by Kellemora on 2008-12-06
Hi John

On a windows machine, when it asks for the password, don't enter anything, just hit the enter key and it should open the file.  If not then use your Ubuntu password and select remember password permanently and then it shouldn't ask for a password anymore.

TTUL
Gary

---

### Post by zwaardmeester on 2008-12-07
When sharing a folder in Nautilus, make sure you enable "Guest Access". 

Hope it helps.

---

