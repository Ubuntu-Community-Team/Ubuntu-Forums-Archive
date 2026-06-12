---
title: "Issue while installing passenger"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Bhupendramishra on 2011-01-18
Please some one help me.. I would be thank ful to them
issue while install curl on ubantu. I followed step as...
$ gem install passenger 
$ passenger-install-apache2-module
got error as follows
* GNU C++ compiler... found at /usr/bin/g++
* Curl development headers with SSL support... not found
* OpenSSL development headers... found
* Zlib development headers... found
* Ruby development headers... found
* OpenSSL support for Ruby... found
* RubyGems... found
* Rake... found at /var/lib/gems/1.8/bin/rake
* rack... found
* Apache 2... found at /usr/sbin/apache2
* Apache 2 development headers... found at /usr/bin/apxs2
* Apache Portable Runtime (APR) development headers... found at /usr/bin/apr-1-config
* Apache Portable Runtime Utility (APU) development headers... found at /usr/bin/apu-1-config
Some required software is not installed.
-----------------------------------------
$ apt-get install libcurl4-openssl-dev
got error as follows
--------------------------------------
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following extra packages will be installed:
libcurl3 libidn11-dev
Suggested packages:
libcurl3-dbg
The following NEW packages will be installed
libcurl4-openssl-dev libidn11-dev
The following packages will be upgraded:
libcurl3
1 upgraded, 2 newly installed, 0 to remove and 346 not upgraded.
Need to get 1700kB of archives.
After this operation, 3293kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
libcurl3 libidn11-dev libcurl4-openssl-dev
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main libcurl3 7.18.2-1ubuntu4.4
404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libcurl3 7.18.2-1ubuntu4.4
404 Not Found [IP: 91.189.92.166 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main libidn11-dev 1.8+20080606-1
404 Not Found
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main libcurl4-openssl-dev 7.18.2-1ubuntu4.4
404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libcurl4-openssl-dev 7.18.2-1ubuntu4.4
404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu4.4_i386.deb) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libi/libidn/libidn11-dev_1.8+20080606-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libi/libidn/libidn11-dev_1.8+20080606-1_i386.deb) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl4-openssl-dev_7.18.2-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl4-openssl-dev_7.18.2-1ubuntu4.4_i386.deb) 404 Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by NightwishFan on 2011-01-18
Ubuntu 8.10 reached end of life on April 30, 2010: [https://lists.ubuntu.com/archives/ubuntu-announce/2010-March/000130.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-March/000130.html)

You will have to upgrade with the processes detailed here. I have never done so myself so I can not advise you on specifics, but feel free to ask if I or someone else can answer. :)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

