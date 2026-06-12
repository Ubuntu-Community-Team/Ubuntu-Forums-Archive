---
title: "samba daemons nmbd [fail]"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2007-10-17
i have had a hellof a time trying to get samba to work here is the read out please help want to transfer files to my windows xp machine 


0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/3823kB of archives.
After unpacking 9400kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  samba
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 232486 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.25a-1noacl_i386.deb) ...
Setting up samba (3.0.25a-1noacl) ...
Starting Samba daemons nmbd                                           [fail][/U]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
---------------------------------------------------------------------------------------------------------------------

red-shield@Federal-Reserve:~$ tail /etc/samba/smb.conf
 
[SYS]
comment = SYS Volume
path = /
valid users = root
public = no
writable = yes
available = yes
browsable = yes

---------------------------------------------------------------------------------------------------------------------

---

### Post by mpokrywka on 2007-10-18
One solution: move away current config file (mv /etc/samba/smb.conf /etc/samba/smb.conf.backup) and try to reinstall samba **apt-get --reinstall install samba**. Then try if your config is valid.
Second solution: edit /var/lib/dpkg/info/samba.postinst file, find lines with "samba start" and replace "|| exit $?" with "|| true". Next **apt-get -f install** should finish installation.
To check validity of your config try: **testparm /your/config-file**

---

