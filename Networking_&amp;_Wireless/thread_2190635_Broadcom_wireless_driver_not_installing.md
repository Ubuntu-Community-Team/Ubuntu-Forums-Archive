---
title: "Broadcom wireless driver not installing"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by c1709348 on 2013-11-28
Hi,

I'm a completely new Linux user and I've installed Ubuntu 12.04.

I'm having a problem with the Broadcom STA wireless drivers, I can't get them to install.

I get the /var/log/jockey.log error

I have looked up many solutions online before, typed many lines into the terminal but nothing has sorted out the problem.

I'd appreciate some help thanks

---

### Post by chili555 on 2013-11-28
How about typing this line in the terminal and tell us the result:```
lspci -nn | grep 0280
```

---

### Post by c1709348 on 2013-11-28
Thanks for replying

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by Lloydb39 on 2013-11-28
I had this problem and it is a pain but it is fixable. My suggestion would be to start here: [http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

---

### Post by c1709348 on 2013-11-28
It looks similar to other methods I have tried but I'll give it a bash, thanks

---

### Post by chili555 on 2013-11-28
> **c1709348 said:**
> It looks similar to other methods I have tried but I'll give it a bash, thanksI suggest a different approach. Please get a temporary wired ethernet connection and open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
```If it isn't installed, that's fine, just continue:```
sudo apt-get install firmware-b43-lpphy-installer
```Detach the ethernet, reboot and let us have your report.

---

### Post by c1709348 on 2013-11-28
This is what I get after 1st command

john@ubuntu:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163512 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
Warning: No support for locale: en_GB.utf8
Setting up avg2013flx (2013.3115) ...
Installing 'avgd' service initscripts...
ln: failed to create symbolic link `/etc/init.d/avgd': File exists
dpkg: error processing avg2013flx (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 avg2013flx
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@ubuntu:~$

---

### Post by c1709348 on 2013-11-28
This is what I get after the 2nd command

john@ubuntu:~$ sudo apt-get install firmaware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmaware-b43-lpphy-installer
john@ubuntu:~$

---

### Post by chili555 on 2013-11-28
> Setting up avg2013flx (2013.3115) ...
Installing 'avgd' service initscripts...
ln: failed to create symbolic link `/etc/init.d/avgd': File exists
dpkg: error processing avg2013flx (--configure):
subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
avg2013flx
E: Sub-process /usr/bin/dpkg returned an error code (1)Arrrgh!! It appears that you have a half-installed version of AVG anti-virus software. I am fairly certain that you did not get this from the Ubuntu repositories and, evidently, it is not installed correctly and can't be configured. Please see a similar case here: [https://answers.launchpad.net/ubuntu/+question/4392](https://answers.launchpad.net/ubuntu/+question/4392)

I think AVG writes a one-size-maybe-possibly-fits-all package. It may work well in 13.10, using the 3.11.0-xx kernel but not at all in 12.04, using the 3.2.0-xx kernel and their respective associated libraries.

I would suggest you get that problem solved first as any attempt to get things installed will fail, as you've seen. I am no expert about AVG so I'd suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

In my 12 years in Linux, I have never installed an anti-virus.

---

### Post by chili555 on 2013-11-28
> E: Unable to locate package firmaware-b43-lpphy-installerIt is firmware, not firmaware.

---

### Post by c1709348 on 2013-11-28
Thanks for the help, I think I shall just reinstall ubuntu. May be back some other day

---

