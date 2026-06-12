---
title: "Failure to connect to windows based network"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by godd4242 on 2007-05-03
Hello all.
Been a while since my last post, but the issue is this.
I can't sign onto my schools wireless network (WLAN)
it has a WPA security code, and when i try to use WiFi Radar to connect, here is my error log:

dhclient3 --version 2>&1
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.
SIOCSIFNETMASK: Cannot assign requested address
SIOCADDRT: Invalid argument

An interesting error to say the least, due to the fact that I'm using my lappies internal wireless card  to post this on my home network.

(the problem seems to be my pc doesn't get an Ip address, wifi radar says connected to x, ip (none)



Anyone got any helps or tips?

---

### Post by dannyboy79 on 2007-05-04
> **godd4242 said:**
> Hello all.
Been a while since my last post, but the issue is this.
I can't sign onto my schools wireless network (WLAN)
it has a WPA security code, and when i try to use WiFi Radar to connect, here is my error log:

dhclient3 --version 2>&1
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.
SIOCSIFNETMASK: Cannot assign requested address
SIOCADDRT: Invalid argument

An interesting error to say the least, due to the fact that I'm using my lappies internal wireless card  to post this on my home network.

(the problem seems to be my pc doesn't get an Ip address, wifi radar says connected to x, ip (none)



Anyone got any helps or tips?

I can't speak for wifi-radar and WPA but I know that editing the files which are used int he background should be able to be edited and you should get connected. follow this guide here and you should be set.

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+with+wpa](http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+with+wpa)

---

