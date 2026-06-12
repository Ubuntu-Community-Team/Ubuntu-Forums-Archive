---
title: "enable monitor mode"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by gizmo720 on 2010-12-12
I am currently running my wireless using the ipw2200 driver. I downloaded the source, whose documentation said that the driver could run in monitor mode (although it is not officially supported) I am still running with the original driver, which might be an earlier version. 

I want to switch to monitor mode. So far i have tried
 ```
sudo iwconfig eth1 mode monitor
```
which causes me to loose network connection and have Ubuntu automatically reconnect in managed mode. 
Any ideas?

---

### Post by t4thfavor on 2010-12-12
You have to suspend networkmanager, if you don't it will detect the drop in network connectivity caused by monitor mode, and then change back to managed mode, and reconnect.

My ipw2200 won't monitor anymore, it stopped working with airmon-ng around ubuntu release 7.04.

EDIT::
Looks like I lied, your command worked fine, I guess I shouldn't have been so lazy.
I would kill networkmanager, and try again.

I used:
```

sudo airmon-ng start eth1

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
886	NetworkManager
898	avahi-daemon
904	avahi-daemon
1007	wpa_supplicant
3080	dhclient
Process with PID 3080 (dhclient) is running on interface eth1


Interface	Chipset		Driver

eth1		Intel 2200BG	ipw2200 - [phy0]mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)


```

---

### Post by n2itive on 2011-03-01
Having the same issue - wondering if you have had any luck

---

### Post by ght12 on 2013-02-20
hi im also having a problem attempting to place my wirless into monitor mode ive tried "sudo airmon-ng start wlan0" and towards the end of the command line it just says " interface         chipset              driver

* doesnt even state any wirless networks... also tried iwconfig and came up with this 
" lo        no wireless extensions
eth0      no wireless extensions" 
im using the ALFA AWUS036NHR USB ADAPTER WITH UNBUNTU. dont have a clue what im doing wrong but i do seem to have internet access thru ubuntu?

---

### Post by wildmanne39 on 2013-02-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

