---
title: "Feisty Networking Improvments...missing?"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by guardsman85 on 2007-04-25
The Ubuntu wiki says that Feisty lists two networking improvements (**[http://tinyurl.com/2vbhey](http://tinyurl.com/2vbhey))--Network Manager **and** Zeroconf.**  I cannot seem to access either of these features.  Any ideas?

I have no idea what to try for commands for Zereconf.

_Here's what I've tried for the network-manager issue:_
I've tried:
 ```
sudo apt-get install network-manager network-manager-gnome
```I'm told that I have the most current version.

Here's what happens when I try to run network-manager:
```
$ sudo network-manager
sudo: network-manager: command not found

```I also tried to locate the network-manager,but I don't think any of these is the binary file:
```
$ locate network-manager
/var/lib/dpkg/info/network-manager.postinst
/var/lib/dpkg/info/network-manager.conffiles
/var/lib/dpkg/info/network-manager-gnome.list
/var/lib/dpkg/info/network-manager-gnome.md5sums
/var/lib/dpkg/info/network-manager-gnome.postrm
/var/lib/dpkg/info/network-manager-gnome.conffiles
/var/lib/dpkg/info/network-manager-gnome.postinst
/var/lib/dpkg/info/network-manager.list
/var/lib/dpkg/info/network-manager.md5sums
/var/lib/dpkg/info/network-manager.prerm
/var/cache/apt/archives/network-manager_0.6.4-6ubuntu7_i386.deb
/var/cache/apt/archives/network-manager-gnome_0.6.4-6ubuntu7_i386.deb
/usr/lib/network-manager
/usr/lib/network-manager/nm-crash-logger
/usr/share/doc/network-manager
/usr/share/doc/network-manager/TODO
/usr/share/doc/network-manager/README
/usr/share/doc/network-manager/README.Debian
/usr/share/doc/network-manager/AUTHORS
/usr/share/doc/network-manager/NEWS.Debian.gz
/usr/share/doc/network-manager/copyright
/usr/share/doc/network-manager/changelog.gz
/usr/share/doc/network-manager/changelog.Debian.gz
/usr/share/doc/network-manager-gnome
/usr/share/doc/network-manager-gnome/TODO
/usr/share/doc/network-manager-gnome/README
/usr/share/doc/network-manager-gnome/AUTHORS
/usr/share/doc/network-manager-gnome/copyright
/usr/share/doc/network-manager-gnome/changelog.gz
/usr/share/doc/network-manager-gnome/changelog.Debian.gz

```

---

### Post by Buffalo Soldier on 2007-04-25
Try:```
nm-applet
``` or ```
nm-applet --sm-disable
```

reference: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by guardsman85 on 2007-04-25
Ahh...now that's an improvement!  I'm more than happy to ditch wifi-radar.  Thanks so much for your help Buffalo Soldier.  I especially appreciate the link to the supporting documentation.  I was able to find Zeroconf information on the same site.

---

### Post by eg-maverick on 2007-04-27
> **Buffalo Soldier said:**
> Try:```
nm-applet
``` or ```
nm-applet --sm-disable
```

reference: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

I tried executing the automatic keyring commands in the above reference without success:
$ sudo apt-get install libpam-keyring
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstlport4.6-dev libmal1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libpam-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.0kB of archives.
After unpacking 131kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe libpam-keyring 0.0.8-5 [16.0kB]
Fetched 16.0kB in 1s (8784B/s)        
Selecting previously deselected package libpam-keyring.
(Reading database ... 170983 files and directories currently installed.)
Unpacking libpam-keyring (from .../libpam-keyring_0.0.8-5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libpam-keyring_0.0.8-5_i386.deb (--unpack):
 trying to overwrite `/lib/security/pam_keyring.so', which is also in package pam-keyring
Errors were encountered while processing:
 /var/cache/apt/archives/libpam-keyring_0.0.8-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


what next?
Craig

---

### Post by jiminycricket on 2007-04-28
That sounds like conflicting packages, yet I can't find a package called "pam-keyring" in Ubuntu's repositories.  This thread also has some advice: [http://ubuntuforums.org/archive/index.php/t-76720.html](http://ubuntuforums.org/archive/index.php/t-76720.html)

---

### Post by eg-maverick on 2007-04-28
> **jiminycricket said:**
> That sounds like conflicting packages, yet I can't find a package called "pam-keyring" in Ubuntu's repositories.  This thread also has some advice: [http://ubuntuforums.org/archive/index.php/t-76720.html](http://ubuntuforums.org/archive/index.php/t-76720.html)

jiminicricket,
Thanks for the post. I looked through it but couldn't find any advice other than to make sure I don't flame :-). I am afraid to use dpkg --force unless I know it won't disable my wifi access. 

The error message above seems to be with trying to overwrite pam_keyring.so. Is it a permission thing? 
Anybody have any ideas?

Craig

---

