---
title: "how to run thise video formats?"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-04-13
although i have vlc,totem and mplayer already installed on my computer,as well as all necessary codecs but non of those apps can open both avi and mov formats??
what to do?

---

### Post by WinterRain on 2010-04-13
In terminal, do: (copy and paste)
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Then:
```
sudo apt-get install non-free-codecs
```

---

### Post by MBG1987 on 2010-04-13
should i edit source.list file to add some repos? cuz i got this eroor:

[PHP]  404  Not Found
Err http://ppa.launchpad.net karmic/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu Sources
  404  Not Found
Err http://ppa.launchpad.net karmic/karmic Sources
  404  Not Found
Err http://www.geekconnection.org karmic/ Release.gpg
  Could not resolve ''
Err http://www.geekconnection.org karmic/ Translation-en_US
  Could not resolve ''
Ign http://dl.google.com stable/non-free Translation-en_US
Ign http://dl.google.com stable/main Translation-en_US
Get:100 http://dl.google.com stable Release [2,540B]
Get:101 http://dl.google.com stable/non-free Packages [1,010B]
Get:102 http://dl.google.com stable/main Packages [913B]
Fetched 1,224kB in 2min 5s (9,794B/s)
Reading package lists...
W: GPG error: http://archive.getdeb.net karmic-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: http://linux.getdropbox.com karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: GPG error: http://deb.torproject.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: GPG error: http://download.virtualbox.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: http://le-web.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A423FD95416E75D
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0DA7581859566E92
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43BB102C405A15CB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC1223EE2314809
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A445E8CCD1A0D2FB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1780999033C3C104
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0D5CCAEDFBD1F9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4D17133CFC5D50C5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 608BF7B93528AE20
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1FFD34C9EB13C954
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/Release.gpg  Could not resolve ''

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/en_US.bz2  Could not resolve ''

W: Failed to fetch http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/karmic/maindeb/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/karmic/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/karmic/karmic/source/Sources.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://packages.medibuntu.org karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://dl.google.com stable/non-free Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_non-free_binary-i386_Packages)
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  libxpp3-java libbackport-util-concurrent-java libjaxme-java libjdom1-java libcommons-codec-java libitext-java libjaxp1.3-java
  libxpp2-java libxerces2-java libjgoodies-looks-java libsidplay1 libitext-java-gcj libjaxen-java
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 310 not upgraded.
Need to get 3,448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 http://packages.medibuntu.org karmic/free medibuntu-keyring 2008.04.20 [3,448B]
Fetched 3,448B in 6s (514B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 147712 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Get:1 http://deb.opera.com lenny Release.gpg [189B]
Ign http://deb.opera.com lenny/non-free Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US
Get:2 http://deb.torproject.org karmic Release.gpg [489B]
Get:3 http://packages.medibuntu.org karmic Release.gpg [197B]
Ign http://packages.medibuntu.org karmic/free Translation-en_US
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US
Get:4 http://archive.getdeb.net karmic-getdeb Release.gpg [835B]
Ign http://archive.getdeb.net karmic-getdeb/apps Translation-en_US
Ign http://archive.getdeb.net karmic-getdeb/games Translation-en_US
Get:5 http://dl.google.com stable Release.gpg [189B]
Hit http://archive.canonical.com karmic Release
Get:6 http://deb.opera.com lenny Release [1,067B]
Get:7 http://packages.medibuntu.org karmic Release [9,237B]
Ign http://download.skype.com stable Release.gpg
Ign http://deb.opera.com lenny Release
Get:8 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:9 http://ppa.launchpad.net karmic Release.gpg [307B]
Get:10 http://le-web.org stable Release.gpg [197B]
Hit http://ly.archive.ubuntu.com karmic Release.gpg
Ign http://ly.archive.ubuntu.com karmic/main Translation-en_US
Ign http://deb.torproject.org karmic/main Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages
Ign http://deb.opera.com lenny/non-free Packages
Get:11 http://archive.getdeb.net karmic-getdeb Release [7,241B]
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Get:12 http://download.virtualbox.org karmic Release.gpg [197B]
Ign http://download.virtualbox.org karmic/non-free Translation-en_US
Ign http://download.skype.com stable/non-free Translation-en_US
Get:13 http://linux.getdropbox.com karmic Release.gpg [489B]
Ign http://linux.getdropbox.com karmic/main Translation-en_US
Ign http://deb.opera.com lenny/non-free Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:14 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://packages.medibuntu.org karmic/free Sources
Hit http://packages.medibuntu.org karmic/non-free Sources
Get:15 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:16 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ly.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://ly.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://ly.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://ly.archive.ubuntu.com karmic-updates Release.gpg
Ign http://ly.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://ly.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://ly.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://ly.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Ign http://archive.getdeb.net karmic-getdeb Release
Hit http://security.ubuntu.com karmic-security Release
Ign http://download.skype.com stable Release
Get:17 http://deb.torproject.org karmic Release [2,226B]
Hit http://deb.opera.com lenny/non-free Packages
Ign http://deb.torproject.org karmic Release
Get:18 http://download.virtualbox.org karmic Release [3,454B]
Ign http://download.virtualbox.org karmic Release
Hit http://archive.getdeb.net karmic-getdeb/apps Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:19 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:20 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:21 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ly.archive.ubuntu.com karmic Release
Hit http://ly.archive.ubuntu.com karmic-updates Release
Hit http://archive.getdeb.net karmic-getdeb/games Packages
Hit http://download.skype.com stable/non-free Packages
Get:22 http://linux.getdropbox.com karmic Release [2,601B]
Hit http://security.ubuntu.com karmic-security/main Packages
Ign http://deb.torproject.org karmic/main Packages
Hit http://download.virtualbox.org karmic/non-free Packages
Ign http://linux.getdropbox.com karmic Release
Get:23 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://deb.torproject.org karmic/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://ly.archive.ubuntu.com karmic/main Packages
Hit http://deb.torproject.org karmic/main Packages
Err http://www.geekconnection.org karmic/ Release.gpg
  Could not resolve ''
Err http://www.geekconnection.org karmic/ Translation-en_US
  Could not resolve ''
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:24 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:25 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:26 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://linux.getdropbox.com karmic/main Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Ign http://le-web.org stable/main Translation-en_US
Hit http://ly.archive.ubuntu.com karmic/restricted Packages
Hit http://ly.archive.ubuntu.com karmic/main Sources
Hit http://ly.archive.ubuntu.com karmic/restricted Sources
Hit http://ly.archive.ubuntu.com karmic/universe Packages
Hit http://ly.archive.ubuntu.com karmic/universe Sources
Get:27 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:28 http://ppa.launchpad.net karmic Release.gpg [307B]
Hit http://ly.archive.ubuntu.com karmic/multiverse Packages
Hit http://ly.archive.ubuntu.com karmic/multiverse Sources
Hit http://ly.archive.ubuntu.com karmic-updates/main Packages
Hit http://ly.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://ly.archive.ubuntu.com karmic-updates/main Sources
Hit http://ly.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://ly.archive.ubuntu.com karmic-updates/universe Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:29 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:30 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:31 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ly.archive.ubuntu.com karmic-updates/universe Sources
Hit http://ly.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://ly.archive.ubuntu.com karmic-updates/multiverse Sources
Get:32 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:33 http://ppa.launchpad.net karmic Release.gpg [307B]
Get:34 http://le-web.org stable Release [5,316B]
Ign http://le-web.org stable Release
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:35 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:36 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:37 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:38 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:39 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:40 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:41 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:42 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:43 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:44 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:45 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Ign http://le-web.org stable/main Packages
Hit http://ppa.launchpad.net karmic Release
Get:46 http://ppa.launchpad.net karmic Release [66.0kB]
Get:47 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Ign http://ppa.launchpad.net karmic Release
Get:48 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:49 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:50 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:51 http://ppa.launchpad.net karmic Release [66.0kB]
Hit http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net karmic Release
Get:52 http://ppa.launchpad.net karmic Release [65.9kB]
Ign http://ppa.launchpad.net karmic Release
Get:53 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:54 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:55 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:56 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:57 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:58 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:59 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:60 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:61 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:62 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:63 http://ppa.launchpad.net karmic Release [65.9kB]
Hit http://ppa.launchpad.net karmic Release
Ign http://ppa.launchpad.net karmic Release
Get:64 http://ppa.launchpad.net karmic Release [66.0kB]
Get:65 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Ign http://ppa.launchpad.net karmic Release
Get:66 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Get:67 http://ppa.launchpad.net karmic Release [66.0kB]
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Ign http://ppa.launchpad.net karmic Release
Get:68 http://ppa.launchpad.net karmic Release [66.0kB]
Get:69 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Ign http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://le-web.org stable/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/maindeb Sources
Hit http://le-web.org stable/main Packages
Ign http://ppa.launchpad.net karmic/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu Sources
Ign http://ppa.launchpad.net karmic/karmic Sources
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/maindeb Sources
Ign http://ppa.launchpad.net karmic/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu Sources
Ign http://ppa.launchpad.net karmic/karmic Sources
Err http://ppa.launchpad.net karmic/maindeb Sources
  404  Not Found
Err http://ppa.launchpad.net karmic/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu Sources
  404  Not Found
Err http://ppa.launchpad.net karmic/karmic Sources
  404  Not Found
Ign http://dl.google.com stable/non-free Translation-en_US
Ign http://dl.google.com stable/main Translation-en_US
Get:70 http://dl.google.com stable Release [2,540B]
Get:71 http://dl.google.com stable/non-free Packages [1,010B]
Get:72 http://dl.google.com stable/main Packages [913B]
Fetched 15.6kB in 2min 5s (124B/s)
Reading package lists...
W: GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: http://archive.getdeb.net karmic-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://deb.torproject.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: GPG error: http://download.virtualbox.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: http://linux.getdropbox.com karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: GPG error: http://le-web.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A423FD95416E75D
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0DA7581859566E92
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43BB102C405A15CB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC1223EE2314809
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A445E8CCD1A0D2FB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1780999033C3C104
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0D5CCAEDFBD1F9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4D17133CFC5D50C5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 608BF7B93528AE20
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1FFD34C9EB13C954
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/Release.gpg  Could not resolve ''

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/en_US.bz2  Could not resolve ''

W: Failed to fetch http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/karmic/maindeb/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/karmic/http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/karmic/karmic/source/Sources.gz  404  Not Found

[/PHP]

---

