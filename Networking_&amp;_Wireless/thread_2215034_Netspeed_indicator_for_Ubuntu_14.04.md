---
title: "Netspeed indicator for Ubuntu 14.04"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by linuxmint7771 on 2014-04-04
I have a 3G mobile broadband connection that keeps changing network speed according to location and time and so I relied heavily on this applet [http://www.webupd8.org/2011/05/how-to-display-network-upload-download.html](http://www.webupd8.org/2011/05/how-to-display-network-upload-download.html) to monitor my netspeed and to choose a good location and time to download big files. Now this applet doesn't seem to run on Ubuntu 14.04 anymore. I love this release and I don't want to relapse into previous releases for this. So I need an alternative to this one that displays netspeed in digits unlike indicator multiload! Any help would be appreciated guys:P

---

### Post by chinmay3 on 2014-04-18
Same is true about me. For last 15 days i am searching for its solution. Please Help us. Thanks in advance:)

---

### Post by Whoopie on 2014-04-19
[https://github.com/mgedmin/indicator-netspeed](https://github.com/mgedmin/indicator-netspeed)

---

### Post by chinmay3 on 2014-04-20
Thanks for your help. I followed commands in above link. Now it shows netspeed-indicator , but it only shows download speed. Is it programmed to show that way?
in ubuntu 13.04 i have installed one such indicator (indicator-sysmon)  which was showing both upload & download as well as ram and cpu usages. Anyway Thanks again.

in meantime i tried again installing indicator-sysmon & now it working but with missing icon. see screenshot.

---

### Post by linuxmint7771 on 2014-04-20
Many thanks!! But how can I install indicator-sysm?

---

### Post by linuxmint7771 on 2014-04-20
I have added this applet to startup applications like this:

cd indicator-netspeed && make && ./indicator-netspeed

but it does not start and so i created a file with this content:

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


#!/bin/bash

cd indicator-netspeed && make && ./indicator-netspeed 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
 and added it to startup applications

---

### Post by mörgæs on 2014-04-20
If this solves your problem please mark the thread so.

---

### Post by chinmay3 on 2014-04-21
search on Webupd8.org. they have article on it.

---

