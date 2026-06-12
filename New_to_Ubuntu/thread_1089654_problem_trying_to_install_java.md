---
title: "problem trying to install java"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by 180turbo on 2009-03-07
Hi Folks,
My 1st post on here, and also my 1st ever Ubuntu install!!!

Installation went fine then after installing the 262 new updates it wanted, i did get an error with something to do with "system-tools-backends".

Anyway, i have downloaded jre-6u12-linux-1585-rpm.bin from Sun and tried to install it but to no avail.

I've had to install rpm but this wont install because of this error...

root@ourpc:/usr/java# apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rpm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

If i can't install rpm then i can't install jre.

Any help on this would be great, but please bear with me as i'm new to the Linux os.

---

### Post by gn2 on 2009-03-07
Welcome to the Ubuntu Forums :)

Reading [this]("http://www.psychocats.net/ubuntu/installingsoftware") will help you understand how to install software in Ubuntu.

.rpm stands for RedHat Package Management, Ubuntu is not based on RedHat and .rpm files are not normally what you would use to install from. Ubuntu is based on Debian and .deb is the norm.

To get Java (and lots of other goodies) installed, follow [this guide]("http://www.psychocats.net/ubuntu/nonfree").

---

### Post by SunnyRabbiera on 2009-03-07
Correct
Instead I personally suggest using the repositories to install java.
Ubuntu has a library of packages called repositories, unlike windows where you have to go to site A, Site 2, Site Z Ubuntu has a centralized place to get packages.
The simplist way to get java is to install the ubuntu restricted extras package.
To install it simply go up to applications then to add/remove and once it is loaded search for the ubuntu restricted extras package, click on the box next to the package name and the rest should be easy to figure out.

---

### Post by 180turbo on 2009-03-07
Ahhh!!!

Thanks guys i did wonder what rpm was for.

Is there a quick way to get to the repositories please?

---

### Post by gn2 on 2009-03-07
Two ways, 

Either: Applications > Add/Remove

Or: System > Administration > Synaptic Package Manager

---

### Post by SunnyRabbiera on 2009-03-07
> **gn2 said:**
> Two ways, 

Either: Applications > Add/Remove

Or: System > Administration > Synaptic Package Manager

Right, both are front ends to apt.
Apt is a tool that helps install and removes packages on a typical Debian system, and on Ubuntu as Ubuntu is based on debian.
Anyhow if there is a package you cannot find in the repositories and if you must go onto the internet for a package the installer format that Ubuntu uses is .deb.
.deb is sort of like the Ubuntu version of a .exe though its more like a .zip installer then a executable.
Avoid RPM if possible, if it is really needed then I suggest trying out alien, though alien is a command line tool it does its job pretty well.

---

### Post by presence1960 on 2009-03-07
> **180turbo said:**
> Hi Folks,
My 1st post on here, and also my 1st ever Ubuntu install!!!

Installation went fine then after installing the 262 new updates it wanted, i did get an error with something to do with "system-tools-backends".

Anyway, i have downloaded jre-6u12-linux-1585-rpm.bin from Sun and tried to install it but to no avail.

I've had to install rpm but this wont install because of this error...

root@ourpc:/usr/java# apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rpm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

If i can't install rpm then i can't install jre.

Any help on this would be great, but please bear with me as i'm new to the Linux os.

are you running 32bit or 64 bit?

If 64 bit try these links, either one works :

[http://ubuntuforums.org/showpost.php...74&postcount=1](http://ubuntuforums.org/showpost.php...74&postcount=1)

[http://ubuntuforums.org/showpost.php...9&postcount=59](http://ubuntuforums.org/showpost.php...9&postcount=59)

---

### Post by 180turbo on 2009-03-08
Thanks for the info. Its 32bit by the way.

I think there's a more serious issue i have in that evrytime i download new updates i get the following error.

 E: system-tools-backends: subprocess post-installation script returned error exit status 1

When i look at the details i see something like this. Not sure why evreytime i install updates i get this error with system-tools-backends. Does it mean that none of the updates has worked?

Errors were encountered while processing:
 system-tools-backends
E: sub-process /usr/bin/dpkg returned error code (1)
A package failed to install. trying to recover:
setting up system-tools-backends (2.6.0-1ubuntu1.1)...
 * starting system tools backends system-tools-backends
invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned errors exist status 1
Errors where encountered while processing:
 system-tools-backends

---

### Post by 180turbo on 2009-03-09
Looks like others are having the same problem...

[http://ubuntuforums.org/archive/index.php/t-976149.html](http://ubuntuforums.org/archive/index.php/t-976149.html)

I'll try un-installing that library and installing again later on.

---

### Post by 180turbo on 2009-03-09
I uninstalled the lib system-tools-backends and reinstalled it, all went well.

i have now installed jre and linked it and can run jre in the browser.

[http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html)

---

