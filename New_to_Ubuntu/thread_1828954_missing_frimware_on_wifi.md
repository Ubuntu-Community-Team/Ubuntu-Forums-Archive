---
title: "missing frimware on wifi"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by carloscortez39 on 2011-08-19
i scene  some post an the say to put this code 

ls -al /lib/firmware/b43

it give me this

total 12
drwxr-xr-x  2 root root 4096 2011-08-19 18:33 .
drwxr-xr-x 58 root root 4096 2011-08-19 18:33 ..
-rw-r--r--  1 root root  179 2011-08-19 18:33 examples.desktop
carlos@carlos-TravelMate-2480:~$ dmesg | grep firmware
[   64.714875] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2487.029889] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2544.778639] b43-phy1 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website

---

### Post by LowSky on 2011-08-20
so do what it says

```
sudo apt-get install b43-fwcutter
```

---

### Post by carloscortez39 on 2011-08-20
it says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main b43-fwcutter i386 1:013-3 [14.6 kB]
Fetched 14.6 kB in 0s (17.6 kB/s) 
Selecting previously deselected package b43-fwcutter.
(Reading database ... 180686 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...

than still say missing firmware

---

### Post by gandaran on 2011-08-21
follow this thread to find the firmware
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by carloscortez39 on 2011-08-21
its give me error when i put 
code
dmesg | grep b43

---

