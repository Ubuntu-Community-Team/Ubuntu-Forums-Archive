---
title: "[SOLVED] Weird errors when trying to run commands in terminal"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by iamcims on 2008-08-24
My wireless happened to get messed up somehow and dissapear, it has happened to me before and re downloading/installing the drivers fixes it. However i am getting an error in my console when I try to do this.


Here is the command I am trying to run.
```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot
```


Here is what happens when I run the code in terminal (root).

```
tim@tim-laptop:~$ su
Password: 
root@tim-laptop:/home/tim# wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
--16:13:23--  http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
           => `madwifi-ng-r2756+ar5007.tar.gz.7'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485           --.--K/s             

16:13:24 (23.15 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.7' saved [485/485]

root@tim-laptop:/home/tim# 
root@tim-laptop:/home/tim# tar xfz madwifi-ng-r2756+ar5007.tar.gz
root@tim-laptop:/home/tim# 
root@tim-laptop:/home/tim# cd madwifi-ng-r2756+ar5007
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# 
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# make
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Stop.
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# 
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# sudo make install
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Stop.
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# 
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# sudo modprobe ath_pci
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# 
root@tim-laptop:/home/tim/madwifi-ng-r2756+ar5007# sudo reboot

```

Thank you for any help. I installed ubuntu studio last night, rebooted many times, and my wireless was fine. I shut my laptop off at about 5am and when I turned it back on I found my wireless was not working.

---

