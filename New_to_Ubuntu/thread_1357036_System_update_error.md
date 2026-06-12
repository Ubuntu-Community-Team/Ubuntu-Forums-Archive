---
title: "System update error"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by mourts on 2009-12-16
Hello,

Everytime I try to do an update I'm able to download all the packages but when ubuntu starts to install them I get this error (snapshot attach)

Any Ideas How I can resolve the problem?
I'm running Ubuntu 9.10 on a Dell Dimension 3100

Thank you

---

### Post by wojox on 2009-12-17
Try:

```
sudo apt-get update && sudo dpkg --configure -a
```

Or:

```
sudo apt-get install -f
```

---

### Post by mourts on 2009-12-17
Thanks for your answer, I tried both and I'm still getting an error

Errors were encountered while processing:
 libdns53
 bind9-host
 ureadahead
 sreadahead
 dnsutils
 libisccfg50
 libbind9-50
adolfo@adolfo-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ureadahead (0.90.3-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ureadahead (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdns53 (1:9.6.1.dfsg.P1-3ubuntu0.2) ...
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
 bind9-host depends on libbind9-50 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libbind9-50 is not configured yet.
 bind9-host depends on libdns53No apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                  (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libdns53 is not configured yet.
 bind9-host depends on libisccfg50 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libisccfg50 is not configured yet.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libbind9-50 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libbind9-50 is not configured yet.
 dnsutils depends on libdns53 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libdns53 is not configured yet.
 dnsutils depends on libisccfg50 (= 1:9.6.1.dfsg.P1-3ubuntu0.2); however:
  Package libisccfg50 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sreadahead:
 sreadahead depends on ureadahead; however:
  Package ureadahead is not configured yet.
dpkg: error processing sreadahead (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ureadahead
 libdns53
 libisccfg50
 libbind9-50
 bind9-host
 dnsutils
 sreadahead
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philinux on 2009-12-17
Open synaptic. Click reload, then mark all upgrades, and then apply. See if it will resolve some of this.

---

### Post by mourts on 2009-12-17
Didn't work either, attached is what I got

Thank you

---

