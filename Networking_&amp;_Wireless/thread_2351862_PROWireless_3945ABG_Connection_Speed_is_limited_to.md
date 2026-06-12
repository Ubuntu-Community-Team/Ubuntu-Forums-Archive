---
title: "PRO/Wireless 3945ABG Connection Speed is limited to 20Mbit"
date: 2017-02-07
forum: Networking &amp; Wireless
---

### Post by hodja on 2017-02-07
Hello,


I have a problem with the download speed of wifi on Ubuntu 16.04.1 LTS, with Intel Corporation PRO/Wireless 3945ABG [Golan] Wifi Module. 


Fiber speed is 50Mbits/s but I can only download with 20Mbits/sec. Other devices on the network can download with full speed (up to 45Mbits/s) 


My Router is a HUAWEI HG255s


Any help will be appreciated. 


Here is the output of the wifi hardware info script: 

[https://paste.ubuntu.com/23947922/](https://paste.ubuntu.com/23947922/)

Thanks

---

### Post by wildmanne39 on 2017-02-07
Have a look at the following thread.
[https://ubuntuforums.org/showthread.php?t=2351152](https://ubuntuforums.org/showthread.php?t=2351152)
do not do the part about the country code for now.

Also in dmesg it shows that your firewall is blocking your post that is also slowing down the connection.

---

