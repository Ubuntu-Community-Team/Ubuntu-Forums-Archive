---
title: "SAMBA problems HELLLLP needed"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by maldojr88 on 2007-07-26
hello...well the problem is that i had samba...and deleted my samba.conf file...
so then some dude told me to uninstall and install back agian
so i unistalled using these commands:

$ sudo apt-get clean
$sudo apt-get remove --purge samba

then i typed

$ sudo apt-get install samba

and i get this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Recommended packages:
smbldap-tools
The following NEW packages will be installed:
samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3341kB of archives.
After unpacking 8184kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main samba 3.0.24-2ubuntu1.2 [3341kB]
Fetched 3341kB in 37s (89.9kB/s)
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 120079 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Setting up samba (3.0.24-2ubuntu1.2) ...
Generating /etc/default/samba...
* Starting Samba daemons... [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kidders on 2007-07-28
Hi there,

It's hard to know the exact cause of the problem you ran into, but suffice it to say, you got bad advice. All that was really required is the recreation of your Samba configuration file, many examples of which are available on the web, and which Ubuntu's package manager is very likely capable of producing for you all by itself. In either case, it *ought* to have been a 10-second job. :-(

The first thing you need to do now is figure out whether your Samba is installed properly. Have a look around your system, and see if you can get a handle on what the story is. If Samba seems okay, create yourself a realllllly basic "does-almost-nothing" configuration file, and see if you can make it start up & serve files. For testing purposes, you might like to temporarily create one completely public, guest-accessible share ... just to convince yourself everything's okay. With any luck, **sudo /etc/init.d/samba restart** will be all you need to do.

---

