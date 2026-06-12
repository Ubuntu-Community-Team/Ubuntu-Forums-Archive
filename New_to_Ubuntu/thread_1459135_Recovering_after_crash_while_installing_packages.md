---
title: "Recovering after crash while installing packages"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2010-04-21
I had to do a hard reset after a crash I just had.  System would not even allow for a terminal login through Ctrl-Alt-F1.  Now, I get the following output when trying to do the upgrades that were in progress when system crashed.  It is a very new install, wondering if it would just be better to wipe and start again, as I have not installed anything other than upgrades.

```
michael@michael-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.31-20-generic (2.6.31-20.58) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ureadahead (0.90.3-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ureadahead (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdns53 (1:9.6.1.dfsg.P1-3ubuntu0.3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdns53 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libisccfg50:
 libisccfg50 depends on libdns53; however:
  Package libdns53 is not configured yet.
dpkg: error processing libisccfg50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbind9-50:
 libbind9-50 depends on libdns53; however:
  Package libdns53 is not configured yet.
 libbind9-50 depends on libisccfg50; however:
  Package libisccfg50 is not configured yet.
dpkg: error processing libbind9-50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libbind9-50 (= 1:9.6.1.dfsg.P1-3ubuntu0.3); however:
  Package libbind9-50 is not configured yet.
 bind9-host depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.3); however:
  Package libdns53 is not configured yet.
 bind9-host depends on libisccfg50 (= 1:9.6.1.dfsg.P1-3ubuntu0.3); however:
  Package libisccfg50 is not configured yet.
dpkg: erNo apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
                                                                                       No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                                                                                        No apport report written because MaxReports is reached already
                                                           ror processing bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libbind9-50 (= 1:9.6.1.dfsg.P1-3ubuntu0.3); however:
  Package libbind9-50 is not configured yet.
 dnsutils depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.3); however:
  Package libdns53 is not configured yet.
 dnsutils depends on libisccfg50 (= 1:9.6.1.dfsg.P1-3ubuntu0.3); however:
  Package libisccfg50 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-20-generic (2.6.31-20.58) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-20-generic; however:
  Package linux-headers-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sreadahead:
 sreadahead depends on ureadahead; however:
  Package ureadahead is not configured yet.
dpkg: error processing sreadahead (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 ureadahead
 libdns53
 libisccfg50
 libbind9-50
 bind9-host
 dnsutils
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-20-generic
 linux-headers-generic
 sreadahead
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by uRock on 2010-04-21
If you have tried booting the restore kernel in the grub menu and you have a /home partition, I'd say go for the reinstall. I prefer fixing the system whenever possible, but sometimes the reinstall is just faster.

---

### Post by k3lt01 on 2010-04-21
At boot when you see the GRUB menu click on "Recovery", it will be the 2nd line. Then another screen will come up and you should click on "dpkg". Follow th instructions and it will attempt to fix any issues that need fixing. After that has all happened reboot into normal mode.

If it still wont boot, it will probably be quicker, as our esteemed friend uRock said, to just do a reinstall.

---

### Post by cdmike2k8 on 2010-04-21
I think I might just go with a re-install, only been up for a few hours...  If there was more to loose, I would try to fix it.  Not worth the effort, seeing as I have not even got anything up and running yet.  Thanks for the response.

---

### Post by uRock on 2010-04-21
I don't know if you know this already, but if you know the names of the programs you have installed, you can make one big command to install them all at once after you get the system reinstalled and updated. Here is a few just for an example, ```
sudo apt-get install thunderbird ubuntu-restricted-extras pidgin epiphany-browser
```
As long as you spell the name right and put one space between each program you can perfect this for future installs.

---

### Post by cdmike2k8 on 2010-04-22
Ya,I know the command line decently well.  I have reinstalled, and am currently going through [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) to get my media set up.  Hopefully no more issues.  I had it hang one time after install again, but this install seems good.  Only thing different hardware wise is that I upgraded ram before reinstall.  System was stable with new ram before I reinstalled OS.  Thought issue might be a bad stick, but they all passed ram check with 5 passes, so I doubt that is the issue.  If the system hangs again, I will be back here, attempting to figure out what is causing the hang right after a clean install.

---

