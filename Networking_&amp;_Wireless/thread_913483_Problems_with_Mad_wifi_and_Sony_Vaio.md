---
title: "Problems with Mad wifi and Sony Vaio"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Mindcrime13 on 2008-09-07
hello, i've been having some problems, with my vaio and atheros card, i mage to get it working with this code:

> wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot

t worked fine till yesterday, that i got no wireless networks, and it looks as everything wireless was  deleted form the computer

so i tried again today and in the process got this:

> candyraver@candyraver-laptop:~$ wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--19:56:30--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485           --.--K/s             

19:56:30 (28.30 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz' saved [485/485]

candyraver@candyraver-laptop:~$ tar xvf madwifi-ng-r2756+ar5007.tar.gz
madwifi-ng-r2756+ar5007/
madwifi-ng-r2756+ar5007/README
candyraver@candyraver-laptop:~$ cd madwifi-ng-r2756+ar5007
candyraver@candyraver-laptop:~/madwifi-ng-r2756+ar5007$ cd madwifi-ng-r2756+ar5007
bash: cd: madwifi-ng-r2756+ar5007: No such file or directory
candyraver@candyraver-laptop:~/madwifi-ng-r2756+ar5007$ tar xvf madwifi-ng-r2756+ar5007.tar.gz
tar: madwifi-ng-r2756+ar5007.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
candyraver@candyraver-laptop:~/madwifi-ng-r2756+ar5007$ sudo apt-get update && sudo aptitude install build-essential
[sudo] password for candyraver: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US        
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy Release.gpg
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy Release
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/main Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/restricted Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/restricted Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/universe Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/universe Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
candyraver@candyraver-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'.  Stop.
candyraver@candyraver-laptop:~/madwifi-ng-r2756+ar5007$ 

and i don't know what to do in this part. since it stop on its own, i dunno why because this worked last time, 

so if anybody can shed in some light, feel free to do so,

thanks!

---

