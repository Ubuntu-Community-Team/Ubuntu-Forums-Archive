---
title: "synaptic package manager problem"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-05-28
I installed a package using synaptic. Then I uninstalled it using the same. Now I am not able to install it again.

Here is the apt-get output

> 
habitat@habitatserver:~$ sudo apt-get install dovecot-imapd 
sudo: unable to resolve host habitatserver
[sudo] password for habitat: 
Reading package lists...
Building dependency tree...
Reading state information...
dovecot-imapd is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libjs-scriptaculous libjs-prototype
  libsieve2-1 tinymce linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 103 not upgraded.
2 not fully installed or removed.
Need to get 0B/630kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 136764 files and directories currently installed.)
Preparing to replace dovecot-imapd 1:1.0.10-1ubuntu5.2 (using .../dovecot-imapd_1%3a1.0.10-1ubuntu5.2_i386.deb) ...
Unpacking replacement dovecot-imapd ...
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing /var/cache/apt/archives/dovecot-imapd_1%3a1.0.10-1ubuntu5.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dovecot-imapd_1%3a1.0.10-1ubuntu5.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by zvacet on 2010-05-28
Try with 

```
sudo dpkg --configure -a
```

and

```
sudo apt-get -f install
```

and 

```
sudo apt-get dist-upgrade
```

to upgrade 103 not upgraded.

---

### Post by Guruprasad on 2010-05-28
Thanks for the reply

Here is the output...

---

