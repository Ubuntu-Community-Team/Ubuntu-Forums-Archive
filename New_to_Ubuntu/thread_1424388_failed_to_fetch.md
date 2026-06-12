---
title: "failed to fetch?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by kakashi_hatake on 2010-03-07
Hello, I've just joined the forum and I have a little experience with computers (I can do simple tasks and I know basic terms) and I'm brand new to ubuntu. 
My problem:
Everything was going just fine, I was enjoying the customization of ubuntu and the overall fell of the new OS, after going to the software center to look for IDLE for python 2.6 I noticed that there wasn't an option to install so I looked online about what to do and I kept hearing that I should update some stuff. I tried to and it returned about half a million errors in the repositories beginning with "failed to fetch" and every way I tried it there was the same thing. I tried in the terminal:
[sudo apt-get update]

it said good things at first like it was working and then it said the same thing and many 404 messages. I don't know what to do, I tried everything I've seen and it didn't work. please help me, I cant install anything, system or otherwise. if you need additional details please request them with the needed code and I'll try to get them out. I'm using my windows machine right now and I need to haul out the dsl modem over to my room to get it on the internet. as for the hardware I can't tell you much, I found two lovely computers by the trash near me, drives pulled out. the processors are Intel Pentium 4 3.0Ghz with 2gigs of ram and a 20 gigabyte hdd (pata) I have some bios trouble but with a guess i seem to have resolved enough to log in using the recovery terminal [bad idea to be guessing when your a root].
I'm no longer using a proxy (?)

Thank you.

---

### Post by MelDJ on 2010-03-08
go to system-administration-software sources
there click on the current software server (on the right of download from)
then select other.
then press select best server.
exit and let it reload and then try installing software

---

### Post by kakashi_hatake on 2010-03-08
I just tried it and it selected a different server than what I used before. The error was mostly the same however the failed to fetch addresses were different. I don't have any important files on this computer, should I just format my disk and reinstall?

---

### Post by da burger on 2010-03-08
Can you browse the net from Ubuntu? If not the reason you can't install software is the system can't download it.

---

### Post by kakashi_hatake on 2010-03-08
I have no problem using the internet, only updating packages and installing new software. if you need to see the errors and ignores i get after ```
  sudo apt-get update 
``` here it is:
```
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Ign http://76.73.4.58 karmic-updates Release.gpg                               
Ign http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://76.73.4.58 karmic-updates/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://76.73.4.58 karmic-updates/main Translation-en_US
Ign http://76.73.4.58 karmic-proposed Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security Release
Ign http://76.73.4.58 karmic-proposed/restricted Translation-en_US
Ign http://76.73.4.58 karmic-proposed/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://76.73.4.58 karmic-backports Release.gpg
Ign http://76.73.4.58 karmic-backports/restricted Translation-en_US
Ign http://76.73.4.58 karmic-backports/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://76.73.4.58 karmic Release.gpg
Ign http://76.73.4.58 karmic/main Translation-en_US
Ign http://76.73.4.58 karmic/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://76.73.4.58 karmic/restricted Translation-en_US
Ign http://76.73.4.58 karmic/multiverse Translation-en_US
Ign http://76.73.4.58 karmic-updates Release
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://76.73.4.58 karmic-proposed Release
Ign http://76.73.4.58 karmic-backports Release
Err http://security.ubuntu.com karmic-security/restricted Packages
  404  Not Found
Ign http://76.73.4.58 karmic Release
Ign http://76.73.4.58 karmic-updates/restricted Packages
Ign http://76.73.4.58 karmic-updates/main Packages
Err http://security.ubuntu.com karmic-security/main Packages
  404  Not Found
Ign http://76.73.4.58 karmic-proposed/restricted Packages
Ign http://76.73.4.58 karmic-proposed/main Packages
Ign http://76.73.4.58 karmic-backports/restricted Packages
Ign http://76.73.4.58 karmic-backports/main Packages
Ign http://76.73.4.58 karmic/main Packages
Ign http://76.73.4.58 karmic/universe Packages
Ign http://76.73.4.58 karmic/restricted Packages
Ign http://76.73.4.58 karmic/multiverse Packages
Ign http://76.73.4.58 karmic/universe Sources
Ign http://76.73.4.58 karmic/main Sources
Ign http://76.73.4.58 karmic/multiverse Sources
Ign http://76.73.4.58 karmic/restricted Sources
Ign http://76.73.4.58 karmic-updates/restricted Packages
Ign http://76.73.4.58 karmic-updates/main Packages
Ign http://76.73.4.58 karmic-proposed/restricted Packages
Ign http://76.73.4.58 karmic-proposed/main Packages
Ign http://76.73.4.58 karmic-backports/restricted Packages
Ign http://76.73.4.58 karmic-backports/main Packages
Ign http://76.73.4.58 karmic/main Packages
Ign http://76.73.4.58 karmic/universe Packages
Ign http://76.73.4.58 karmic/restricted Packages
Ign http://76.73.4.58 karmic/multiverse Packages
Ign http://76.73.4.58 karmic/universe Sources
Ign http://76.73.4.58 karmic/main Sources
Ign http://76.73.4.58 karmic/multiverse Sources
Ign http://76.73.4.58 karmic/restricted Sources
Err http://76.73.4.58 karmic-updates/restricted Packages
  404  Not Found
Err http://76.73.4.58 karmic-updates/main Packages
  404  Not Found
Err http://76.73.4.58 karmic-proposed/restricted Packages
  404  Not Found
Err http://76.73.4.58 karmic-proposed/main Packages
  404  Not Found
Err http://76.73.4.58 karmic-backports/restricted Packages
  404  Not Found
Err http://76.73.4.58 karmic-backports/main Packages
  404  Not Found
Err http://76.73.4.58 karmic/main Packages
  404  Not Found
Err http://76.73.4.58 karmic/universe Packages
  404  Not Found
Err http://76.73.4.58 karmic/restricted Packages
  404  Not Found
Err http://76.73.4.58 karmic/multiverse Packages
  404  Not Found
Err http://76.73.4.58 karmic/universe Sources
  404  Not Found
Err http://76.73.4.58 karmic/main Sources
  404  Not Found
Err http://76.73.4.58 karmic/multiverse Sources
  404  Not Found
Err http://76.73.4.58 karmic/restricted Sources
  404  Not Found
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://76.73.4.58/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Repository problem?
I tried visiting the addresses of the error sites and they just prompted me with a download. any ideas?

---

### Post by MelDJ on 2010-03-09
i dont think you need to reinstall because this is most probably server related

---

### Post by kakashi_hatake on 2010-03-09
It would seem so. No sources have worked so far that I tried, I thought maybe a file was corrupted.

---

### Post by MelDJ on 2010-03-09
404 errors shouldn't be the os's fault. 
you could try other servers
or if you are impatient, reinstall

---

### Post by kakashi_hatake on 2010-03-09
I guess i'll just keep trying servers, none have worked so far. thanks.

---

### Post by kakashi_hatake on 2010-03-09
Thanks for trying to help everyone. I must have messed up the apt files. [solved]

---

### Post by ali98ir on 2010-04-02
I also have the same problem using Karmic 9.10. The Internet access is fine but it fails to fetch from repository (404). I haven't changed any setting but since this morning cannot update any file.

Any idea?

Thanks,
Ali

Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/universe/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/karmic/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/karmic/free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/source/Sources.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/karmic/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/karmic/non-free/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

