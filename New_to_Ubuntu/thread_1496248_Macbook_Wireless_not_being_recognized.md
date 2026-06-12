---
title: "Macbook Wireless not being recognized"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by littlboz on 2010-05-29
Hello everyone, I am using Macbook OS X 10.6.3 which I am dual booting with Ubuntu Karmic Koala. I found out my wireless card:

matthew@Matt-Ubuntu:~$ lspci -nn | grep Net
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)

My question is how to get it to work? My network connection do not see it.

---

### Post by unmole on 2010-05-29
_**Ultra Easy Way to get Broadcom STA compatible card working.**_

1) Download [this installer .]("http://docs.google.com/leaf?id=0B73yM4iNvLLlZDM3MThhZDctZjYyOC00NGZhLTlkMjUtZDczZGJmZmMwMTYx&hl=en") using OS X and copy it to a pen drive.

2) Boot into Ubuntu, extract the archive it and open the resulting folder.

3) Double Click on install.sh and choose "Run in Terminal"

4)Follow on screen instructions.

5)Done!

P.S. When you are asked for your password, the password will not be displayed on screen.

---

### Post by littlboz on 2010-05-29
hmmm didn't seem to work but I also can't properly turn of my computer, I made another thread though about that :-p.

I personally don't think the computer not able to turn of properly was the problem

Here is what the terminal says:
Broadcom STA Driver offline installer
for Ubuntu 9.10

by the VigGLUG


Are you sure you want to install this?
Press ENTER to continue

Please do not interrupt the installer...
[sudo] password for matthew: 
dpkg: error processing ./packages/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
(Reading database ... 113657 files and directories currently installed.)
Preparing to replace dkms 2.1.0.1-0ubuntu1 (using .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace dpkg-dev 1.15.4ubuntu2 (using .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Unpacking replacement dpkg-dev ...
dpkg: error processing ./packages/fakeroot_1.12.4ubuntu1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./packages/g++_4.4.1-1ubuntu2_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./packages/g++-4.4_4.4.1-4ubuntu8_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./packages/libstdc++6-4.4-dev_4.4.1-4ubuntu8_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./packages/patch_2.5.9-5_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Setting up dkms (2.1.0.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.31-14-generic   [ OK ] 

dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on patch (>= 2.2-1); however:
  Package patch is not installed.
dpkg: error processing dpkg-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Errors were encountered while processing:
 ./packages/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
 ./packages/fakeroot_1.12.4ubuntu1_i386.deb
 ./packages/g++_4.4.1-1ubuntu2_i386.deb
 ./packages/g++-4.4_4.4.1-4ubuntu8_i386.deb
 ./packages/libstdc++6-4.4-dev_4.4.1-4ubuntu8_i386.deb
 ./packages/patch_2.5.9-5_i386.deb
 dpkg-dev







The package Broadcom STA Driver should now be installed!

All finished here! Reboot your system and you should have a working WiFi...

---

### Post by littlboz on 2010-05-29
Any other suggestions? Maybe this wireless card isn't supported? I hope not, that would be terrible.


I also tried typing in the following command, I heard it would help but it didn't atleast, I don't know how to go about doing it 
matthew@Matt-Ubuntu:~$ sudo apt-get install b43-fwcutter
[sudo] password for matthew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg-dev: Depends: patch (>= 2.2-1) but it is not going to be installed
            Recommends: build-essential but it is not going to be installed
            Recommends: fakeroot but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
matthew@Matt-Ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by littlboz on 2010-05-29
woot I got it. I was exepecting some wicked terminal commands but instead all what I had to do was go to system< adminstrator<hardware drivers

This sit helped out alot:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDevice%2FAirportExtreme](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDevice%2FAirportExtreme)

---

