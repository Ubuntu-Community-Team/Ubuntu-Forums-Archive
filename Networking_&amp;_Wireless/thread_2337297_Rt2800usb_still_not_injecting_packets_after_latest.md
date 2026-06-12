---
title: "Rt2800usb still not injecting packets after latest backports install."
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by csbova on 2016-09-16
Hello everyone!

I'm new to the community and for the past week have been reading through loads of posts regarding various incredibly cool things you can do with linux.
Here's where I am at.

The latest thing I want to do is test my WAP security in my BnB and restaurant.
As a result I have installed aircrack-ng and reaver.
Basic I know, but I'm still new.


My internal wireless card is capable of injecting packets and testing the WAP security which is now impenetrable by these techniques. 
However, in the process of trying to crack my wifi, I have found that my usb wifi rt2800 usb rl2870/3070 was incapable of injecting packets in aireplay-ng.
 [ ```
description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlx00c0ca5958fe
       serial: 00:c0:ca:59:58:fe
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rt2800usb  driverversion=4.4.0-36-generic firmware=0.29 ip=192.168.0.100 link=yes  multicast=yes wireless=IEEE 802.11bgn
```]



So for the sake of learning/challenge [IMG]https://ubuntuforums.org/images/icons/icon6.png[/IMG] I followed the steps to install the latest backports (4.2.0-32) which were supposed to have patched the adapter, making it capable of packet injection.

After running aireplay again, still nothing

[```
$ sudo aireplay-ng -9 mon0
13:43:02  Trying broadcast probe requests...
13:43:04  No Answer...
13:43:04  Found 2 APs

13:43:04  Trying directed probe requests...
13:43:04  DC:D9:16:A4:0F:D7 - channel: 9 - 'VodafoneMobileWiFi-0FD784'
13:43:10   0/30:   0%

13:43:10  3C:1E:04:92:21:64 - channel: 10 - 'D-Link'
13:43:16   0/30:   0%
```]

Does anyone have any ideas? Maybe something obvious that I haven't tried yet?

---

### Post by howefield on 2016-09-16
Thread moved to the "*Networking & Wireless*" forum and closed.

[Forums Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules").
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

