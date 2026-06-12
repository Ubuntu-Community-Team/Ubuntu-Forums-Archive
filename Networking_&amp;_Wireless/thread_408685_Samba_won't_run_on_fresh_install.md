---
title: "Samba won't run on fresh install"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by ThaNerd on 2007-04-13
I've spent a few hours tryin to install Samba. With no luck, so far...

_**1. My config:**_
I'm on a weak computer. AMD Duron, 256Mb RAM, 4 hard disks.

I'm under Edgy. Most of my changes since the "default" installation are a LAMP setup and the addition of a pair of website that are directly accessed from the web.

_**2. My problem:**_
Below, see a "paste" of how i did my install. Please note that i tried several times to install/remove/clean it all.

Also, i'm in a french-speaking environment, so i tried to approximately translate french text to english. Don't mind if some words are not exactly what's supposed to appear. The meaning is still there.

```
thanerd@ThaNerd-idler:/var/poi$ sudo apt-get clean
thanerd@ThaNerd-idler:/var/poi$ sudo apt-get autoclean
Reading list of packets... Done
Building dependancy tree
Reading state of information... Done
thanerd@ThaNerd-idler:/var/poi$ sudo apt-get install samba
Reading list of packets... Done
Building dependancy list
Reading state of information... Done
Recommended packets :
  smbldap-tools
The following NEW packets will be installed :
  samba
0 updated, 1 newly installed, 0 to be removed and 0 not updated.
It is required to take 3028kb in archives.
After unpacking, 7569kb more disk space will be used.
Receiving : 1 http://security.ubuntu.com edgy-security/main samba 3.0.22-1ubuntu4.1 [3028kB]
3028ko received in 8s (351ko/s)
Preconfiguration of packets...
Selection of the packet samba previously unselected.
(Reading database... 118688 Files and folders yet installed.)
Unpacking of samba (from .../samba_3.0.22-1ubuntu4.1_i386.deb) ...
Setting of samba (3.0.22-1ubuntu4.1) ...
 * Starting Samba daemons...                                       [[COLOR="Red"]fail[/COLOR]]
invoke-rc.d: initscript samba, action "start" failed.
dpkg : Processing error of samba (--configure) :
 the sub-process of post-installation script returned an error of status 1
Errors were met when starting :
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
thanerd@ThaNerd-idler:/var/poi$

```

After this, i tried testparm, which returned:
```
thanerd@ThaNerd-idler:/var/poi$ testparm
Load smb config files from /etc/samba/smb.conf
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
        No such file or directory
Error loading services.

```

And well, the file is not there... Not even the /etc/samba folder anyway.

Would anyone have hints or directions? Where else could i search for a cause?

---

### Post by ThaNerd on 2007-04-14
I've spent a few more hours trying to install it, but still no luck... I really need help!

---

