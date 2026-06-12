---
title: "Can't get AIRODUMP working"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by pozeidon on 2016-07-31
Greetings! 

I'll admit off the bat that I'm new to ethical hacking, and I'm having trouble with aircrack-- can't get airodump to open correctly. Please see below....

[B]poseidon@root:~$ sudo airmon-ng start wlan1
[sudo] password for poseidon: 
[/B]

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
2767    avahi-daemon
2781    avahi-daemon
2789    NetworkManager
2941    wpa_supplicant
6909    dhclient
Process with PID 6909 (dhclient) is running on interface wlp3s0


Interface    Chipset        Driver

wlp3s0        Intel AC    iwlwifi - [phy0][B]
poseidon@root:~$ sudo airodump-ng mon0[/B]
Interface mon0: 
ioctl(SIOCGIFINDEX) failed: No such device
poseidon@root:~$ 

Can anyone tell me what I'm doing wrong? I can't find anything online.  Thanks a million for any help!!! :-)

---

### Post by wildmanne39 on 2016-07-31
Hello this is not a supported topic on the forum so I closed your thread!

You should try the aircrack or kali forum.
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

---

