---
title: "Help With Moblock and Mepis"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Nsignificant on 2007-11-04
I am using SimplyMepis 6.5. I know this is not the Mepis forum, but most of the write ups on moblock are from this forum so I thought I would ask here. I cannot download it, here is a log of all the times I tried to on Konsole:
> 
Password:
root@1[Pieter]# ./MoBlock-nfq.sh &
[1] 6760
bash: ./MoBlock-nfq.sh: No such file or directory
root@1[Pieter]# ./home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh &
[2] 6850
[1]   Exit 127                ./MoBlock-nfq.sh
bash: ./home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh: No such file or directory
root@1[Pieter]# /home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh &
[3] 6875
[2]   Exit 127                ./home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh
root@1[Pieter]# /home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh: line 88: ./moblock: No such file or directory
/home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh &
[4] 6990
[3]   Done                    /home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh
root@1[Pieter]# /home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh: line 88: ./moblock: No such file or directory

[4]+  Done                    /home/Pieter/Desktop/MoBlock-0.8/MoBlock-nfq.sh
root@1[Pieter]#
root@1[Pieter]#
root@1[Pieter]# gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 9072870B: public key "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
root@1[Pieter]# gpg --export --armor 9072870B | sudo apt-key add -
OK
root@1[Pieter]# nano etc/apt/sources.list
root@1[Pieter]# nano /etc/apt/sources.list
root@1[Pieter]# sudo apt-get update
Get:1 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Get:2 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Get:4 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:8 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty Release [1803B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Get:9 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty/main Packages [990B]
Get:10 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) feisty/main Sources [683B]
Fetched 3671B in 2s (1643B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@1[Pieter]# sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
E: Broken packages
root@1[Pieter]# nano /etc/apt/sources.list
root@1[Pieter]# sudo apt-get update
Get:1 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Get:2 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release.gpg [189B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:8 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release [1799B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Get:9 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages [983B]
Get:10 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources [735B]
Fetched 3712B in 1s (2289B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@1[Pieter]# sudo apt-get install moblock-nfq
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@1[Pieter]# gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@1[Pieter]# gpg --export --armor 9072870B | sudo apt-key add -
OK
root@1[Pieter]# sudo apt-get update
Get:1 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Get:2 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release.gpg [189B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Fetched 7B in 1s (5B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@1[Pieter]# sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
E: Broken packages
root@1[Pieter]# nano /etc/apt/sources.list





Use "fg" to return to nano

[1]+  Stopped                 nano /etc/apt/sources.list
root@1[Pieter]# sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
^[[ASome packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
E: Broken packages
root@1[Pieter]# nano /etc/apt/sources.list
root@1[Pieter]# sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
E: Broken packages
root@1[Pieter]# gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
^[[A^[[A^[[A^[[Agpg: key 9072870B: "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@1[Pieter]# gpg --export --armor 9072870B | sudo apt-key add -
OK
root@1[Pieter]# sudo apt-get update
Get:1 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Get:2 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Get:3 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release.gpg [189B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Fetched 7B in 1s (5B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@1[Pieter]# sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  moblock-nfq: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libnetfilter-queue1 (>= 0.0.12) but it is not installable
               Depends: libnfnetlink1 (>= 0.0.16) but it is not installable
E: Broken packages
root@1[Pieter]# gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@1[Pieter]# gpg --export --armor 9072870B | sudo apt-key add -
OK
root@1[Pieter]# sudo apt-get update
Get:1 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Get:2 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]
Get:3 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release.gpg [189B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch Release
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) etch/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Fetched 7B in 1s (6B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@1[Pieter]# sudo apt-get install moblock-nfq
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@1[Pieter]#


Any help on this would be very much appreciated.
Note, I am an uber newb :D So please keep it in idiot speak please.
~Thanks again, Pieter.

---

