---
title: "Apt"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by lotusalive on 2010-06-04
RELOAD in Synaptic results in this Error Msg:  Problem executing scripts APT::Update::Pre-Invoke '/usr/bin/daptup --pre'Sub-process returned an error code

I've had trouble installing the latest Jaunty Updates, so I removed what I thought was unnecessary APT software, then Updates installed just fine.  

When I went back to Synaptics, everything looked great, until I hit RELOAD, then the above error message resulted.  I have no Quick Search or Canonical Supported Pkg Highlights.  I removed the 'daptup' pkg successfully, but the same error msg, and non-working aspects of Syn Pkg Mgr still occur.

Suggestions on how to fix appreciated.

---

### Post by oldos2er on 2010-06-04
> **lotusalive said:**
> I've had trouble installing the latest Jaunty Updates, so I removed what I thought was unnecessary APT software, then Updates installed just fine.  


Exactly which software did you remove? What trouble were you having before that?

---

### Post by barney385 on 2010-06-04
aptitude -f install

---

### Post by lotusalive on 2010-06-04
Thanks oldos2er.  As far as apt s/w I removed, before installing Updates from Mgr successfully, I'll have to go make a list for you.  Only apt s/w removed was from 'Universe' only.

This is what Update Mgr gave me before I uninstalled any apt s/w:

**_Update Mgr results in these Error Msgs_**:

**_Check For Updates Results in Error Msg_**: 

E: Problem executing scripts APT::Update::Post-Invoke '/usr/bin/daptup --post'
E: Sub-process returned an error code

**_And upon request to Install_**:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-19_2.6.28-19.61_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-19_2.6.28-19.61_all.deb)

  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-19-generic_2.6.28-19.61_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-19-generic_2.6.28-19.61_i386.deb)

  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.19.24_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.19.24_i386.deb)

  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-server_2.6.28.19.24_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-server_2.6.28.19.24_i386.deb)

  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-server_2.6.28.19.24_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-server_2.6.28.19.24_i386.deb)

  Could not resolve 'us.archive.ubuntu.com

---

### Post by oldos2er on 2010-06-04
Have you tried changing servers? System, Administration, Software Sources, click the drop-down menu next to 'Download from:' Other, Select best server.

---

### Post by lotusalive on 2010-06-04
You guys are the best :)  That command fixed it, and here are the terminal results, so you can see:

lightening@lightening-desktop:~$ aptitude -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
lightening@lightening-desktop:~$ sudo su
[sudo] password for lightening: 
root@lightening-desktop:/home/lightening# aptitude -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  mediamate 
The following NEW packages will be installed:
  libnspr4-dev 
The following packages will be REMOVED:
  attr{u} binutils-multiarch{u} debtags{u} dpkg-cross{u} 
  libclass-methodmaker-perl{u} libconfig-auto-perl{u} 
  libdebian-dpkgcross-perl{u} libfile-homedir-perl{u} 
  libterm-progressbar-perl{u} python-fuse{u} python-twisted-web2{u} 
0 packages upgraded, 2 newly installed, 11 to remove and 0 not upgraded.
Need to get 479kB of archives. After unpacking 29.5MB will be freed.
The following packages have unmet dependencies:
  mediamate: Depends: libphp-adodb but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mediamate [Not Installed]

Score is 119

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be installed:
  libnspr4-dev 
The following packages will be REMOVED:
  attr{u} binutils-multiarch{u} debtags{u} dpkg-cross{u} 
  libclass-methodmaker-perl{u} libconfig-auto-perl{u} 
  libdebian-dpkgcross-perl{u} libfile-homedir-perl{u} 
  libterm-progressbar-perl{u} python-fuse{u} python-twisted-web2{u} 
0 packages upgraded, 1 newly installed, 11 to remove and 0 not upgraded.
Need to get 263kB of archives. After unpacking 30.6MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnspr4-dev 4.7.5-0ubuntu0.9.04.1 [263kB]
Fetched 263kB in 1s (159kB/s)        
(Reading database ... 463051 files and directories currently installed.)
Removing attr ...
Removing dpkg-cross ...
Removing binutils-multiarch ...
Removing `diversion of /usr/bin/size to /usr/bin/size.single by binutils-multiarch'
Removing `diversion of /usr/bin/objdump to /usr/bin/objdump.single by binutils-multiarch'
Removing `diversion of /usr/bin/ar to /usr/bin/ar.single by binutils-multiarch'
Removing `diversion of /usr/bin/strings to /usr/bin/strings.single by binutils-multiarch'
Removing `diversion of /usr/bin/ranlib to /usr/bin/ranlib.single by binutils-multiarch'
Removing `diversion of /usr/bin/objcopy to /usr/bin/objcopy.single by binutils-multiarch'
Removing `diversion of /usr/bin/addr2line to /usr/bin/addr2line.single by binutils-multiarch'
Removing `diversion of /usr/bin/readelf to /usr/bin/readelf.single by binutils-multiarch'
Removing `diversion of /usr/bin/nm to /usr/bin/nm.single by binutils-multiarch'
Removing `diversion of /usr/bin/strip to /usr/bin/strip.single by binutils-multiarch'
Removing `diversion of /usr/bin/gprof to /usr/bin/gprof.single by binutils-multiarch'
Removing `diversion of /usr/lib/libbfd.a to /usr/lib/libbfd-single.a by binutils-multiarch'
Removing `diversion of /usr/lib/libopcodes.a to /usr/lib/libopcodes-single.a by binutils-multiarch'
Removing debtags ...
Removing libterm-progressbar-perl ...
Removing libclass-methodmaker-perl ...
Removing libdebian-dpkgcross-perl ...
Removing libconfig-auto-perl ...
Removing libfile-homedir-perl ...
Removing python-fuse ...
Removing python-twisted-web2 ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 461913 files and directories currently installed.)
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.5-0ubuntu0.9.04.1_i386.deb) ...
Setting up libnspr4-dev (4.7.5-0ubuntu0.9.04.1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

root@lightening-desktop:/home/lightening#

---

### Post by lotusalive on 2010-06-04
P.S. I did go get libphp-adodb, installed fine, but I have a couple questions if you're still there:

1) How do I update php.ini file ?  [Where can I find it ? And does that mean that I should change the code in the file from: /usr/share/adodb to /usr/share/php/adodb ?]

2)  Incidental to installing this: 
debconf: unable to initialize frontend: Dialog  ...   

debconf: falling back to frontend: Readline

Should I fix this, and how ?

---

