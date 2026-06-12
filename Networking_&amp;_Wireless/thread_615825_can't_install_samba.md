---
title: "can't install samba"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Tone1 on 2007-11-17
Absolute beginner! I have a windows xp pc and an abuntu pc networked together (Ubuntu 7.10). I can see the shared files on the xp pc and transfer files to it from ubuntu, I even got the shared printer to work. From the xp pc I can't see the ubuntu pc at all. I tried setting up a shared folder on ubuntu but got the message "Sharing services not installed" it offered me the option to install Unix network support (NFS) and windows network support (SMB) but when I tried the same message just comes back after a couple of seconds. Reading the help I tried installing Samba through terminal. This didn't work either see below :-

tl@Linux:~$ sudo apt-get install samba smbclient
[sudo] password for tl:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate


tl@Linux:~$ sudo apt-get install smbclient samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tl@Linux:~$ 


tl@Linux:~$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

No idea what to do now - hope I'm not being stupid.

---

### Post by HermanAB on 2007-11-17
Go to the Samba web site. Everything you need is right there, including a link to an Ubuntu guide.  Do read the Official Howto.

Cheers,

Herman

---

### Post by Brautigam on 2007-11-17
yes they have a complete guide with faq and everything, it will be easy to understantd

---

### Post by mumm-ra on 2008-01-27
Dude, I just had this problem and it was because I didn't have the newest apt-get packages.


Make sure you're internet connection is working.  Then run sudo apt-get update.  Then you can run sudo apt-get samba smbfs

---

