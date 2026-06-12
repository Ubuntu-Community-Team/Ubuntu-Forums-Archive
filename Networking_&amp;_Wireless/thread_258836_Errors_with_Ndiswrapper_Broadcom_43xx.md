---
title: "Errors with Ndiswrapper Broadcom 43xx"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Scroughan on 2006-09-16
Hey everyone im brandnew to ubuntu and am completely lost trying to get my wireless card to work i keep on gettting strange error  messages and none of the guides have and info on them so im wondering if anyone can help me out. My laptops  a dell 9100 inspirion and im runnign the latest version of ubuntu(fresh install) dua boting with windows.
anyways heres the terminal output;

sean@Ubuntu:~$ sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.
sean@Ubuntu:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
sean@Ubuntu:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 172 not upgraded.
Need to get 0B of archives.
After unpacking 139kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
sean@Ubuntu:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 172 not upgraded.
Need to get 0B of archives.
After unpacking 139kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
sean@Ubuntu:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 172 not upgraded.
Need to get 0B of archives.
After unpacking 139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 69535 files and directories currently installed.)
Removing ndiswrapper-utils ...
sean@Ubuntu:~$ sudo rm -r /etc/modprobe.d/ndiswrapper
sean@Ubuntu:~$ sudo ndiswrapper -e bcmwl5
sudo: ndiswrapper: command not found

##################ok so all clean ready for install############

sean@Ubuntu:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Installing bcmwl5
**couldn't copy /home/sean/Desktop/bcmwl5.inf at /usr/sbin/ndiswrapper line 135.**
sean@Ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  **invalid driver!**
sean@Ubuntu:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
sean@Ubuntu:~$ sudo modprobe ndiswrapper
**FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Invalid argument**


################################################################

anyone got any idea on how to solve this? any help would be greatly appreciated

---

### Post by sjieke on 2006-09-19
A could howto on ndiswrapper can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29")

Try following those instructions, hope it helps

---

