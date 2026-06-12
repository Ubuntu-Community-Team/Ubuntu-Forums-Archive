---
title: "Package manager"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by undo123 on 2011-08-12
Hi everyone.

I have just dun clean install of ubuntu 11.4 on an 80g heard drive. All was well apart from a comment that thunderbird did not install properly.
Now I can not get the package manager to open, I have tried apt-get, deleting the file but nothing seems to work.
Any idea anyone.

JSK

---

### Post by arochester on 2011-08-12
Connect to the Internet. Open a Terminal. Try inputing the following commands one at a time:
> sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove Does it work? Do you get any error messages?

---

### Post by oldos2er on 2011-08-12
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and copy and paste the output here?

---

### Post by undo123 on 2011-08-12
Sorry had to make the dinner.

Here is the list 
 Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Translation-en_GB
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_GB
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_GB
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 thunderbird-globalmenu : Depends: thunderbird (= 3.1.9+nobinonly-0ubuntu4) but 3.1.11+build2+nobinonly-0ubuntu0.11.04.1 is installed
E: Unmet dependencies. Try using -f.

---

### Post by oldos2er on 2011-08-12
Run ```
software-properties-gtk
``` and remove the CD-ROM from your sources. Then run ```
sudo apt-get install -f
```

---

