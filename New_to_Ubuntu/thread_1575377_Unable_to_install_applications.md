---
title: "Unable to install applications"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by m455 on 2010-09-15
I'm new to Ubuntu (first post) and have been more than satisfied with it so far. I've recently ran into a problem installing applications though. What led up to the issue last week I tried to install wireshark and it never fully installed. Now I am getting a "Error Broken count >0" error message stating to start Package Manager.
 
System / Administration / Synaptic Package Manager then gives the error: You Have 1 Broken package on your system! Use the “Broken” filter to locate it.  When I search under broken it shows “smbclient” when I try to mark it for removal and apply it states that not all changes and updates succeeded. The details show the following:

(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up grub-pc (1.98-1ubuntu7) ...
Installation finished. No error reported.
cp: reading `/usr/share/grub/unicode.pf2': Input/output error
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
 
I've tried several things posted in forums to resolve the issue, but nothing seems to work.

---

### Post by rockerphil on 2010-09-15
this may or may not work, but it's worth a shot. try running this command in a terminal

```
sudo apt-get -f install
```

that should fix any broken packages that didn't get to completely install. please feel free to ask any more questions. 

Phil

---

### Post by m455 on 2010-09-15
Thanks.I think I had tried running that previously and got the same result. Here is what it returned with:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-common smbclient
Suggested packages:
  smbfs
The following packages will be upgraded:
  samba-common smbclient
2 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
Need to get 11.9MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main smbclient 2:3.4.7~dfsg-1ubuntu3.2 [11.5MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main samba-common 2:3.4.7~dfsg-1ubuntu3.2 [396kB]
Fetched 11.9MB in 45s (261kB/s)                                                
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

