---
title: "Unable to Start SAMBA after Install"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by nexist on 2006-11-02
Hello:

I wiped my system and installed Edgy.  Whenever I try to add Samba so as to share between my various systems, I get the following error:

```
nexist@SPENGLER:~$ sudo apt-get -f install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  bind9 gdhcpd gbindadmin libmikmod2 dhcp3-server proftpd xmms gproftpd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu4) ...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help would be appreciated.

---

### Post by nexist on 2006-11-05
I am still having this problem, is there any resolution?

---

### Post by nexist on 2006-11-05
Never mind, it seems to have automagically installed this time.

---

