---
title: "internet connection sharing"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by smith19 on 2007-08-17
Hello , i currently  have two pc's the first one is Dell Vista laptop and the second one is ubuntu. i have a Dial-up connection on vista not on ubuntu. and i want to share vista internet to ubuntu and i googled about ICS but no luck here what i did.

 vista ip 192.168.0.1
         subnet mask 255.255.255.0

 ubuntu ip 192.168.0.2
             subnet mask 255.255.255.0
             gateway 192.168.0.1

 i also checked option of "Allow other network users to connect through this computer's internet connection " on vista.

please help me out, i really need internet on ubuntu.

---

### Post by ihristov on 2007-08-17
This is a problem in Vista, not in Ubuntu.

In Ubuntu all you have to do is specify the Vista machine as your gateway, which apparently you have already done.

Well, one more thing you need to do is update your /etc/resolv.conf to specify appropriate DNS servers. Have you done that?

Without involving DNS in any case you should make sure the follwoing things work when you are in Ubuntu

1) ping 192.168.0.1 - this makes sure you have connectivity at all

2) ping your ISP gateway and/or DNS server

3) ping a competely external address: say 66.94.234.13 (yahoo.com)

---

### Post by smith19 on 2007-08-17
I didn't specify DNS servers for /etc/resolv.conf and how do i know my DNS? 
the other thing is i tried ping 192.168.0.1 it's look working, but ping 66.94.234.13 doesn't work. it will not response anything.

---

### Post by smith19 on 2007-08-18
any idea please.:confused::confused:

---

### Post by smith19 on 2007-08-19
finally it work's!
here is  what i did , i added 128.95.120.1 in to /etc/resolv.conf . thanks very much. 
another thing is i am getting another error when i try sudo apt-get update

esmael@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

please help me out .

---

### Post by kevinatkins on 2007-08-19
Hi,

That looks like it might be a firewall issue on Vista - just noticed the update service seems to be running on port 8080, which Vista might be denying.... Try allowing port 8080 and see what happens..

---

### Post by smith19 on 2007-08-19
ok i opened 8080 port, but now it says

esmael@ubuntu:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ihristov on 2007-08-19
I might be mistaken, but it seems to me from the error from 2 posts ago about port 8080 that you have setup an HTTP proxy on your Linux machine.

Try disabling this. If your gateway is configured correctly it should be sufficient.

Can you browse and other Internet web sites from the Linux box?

---

