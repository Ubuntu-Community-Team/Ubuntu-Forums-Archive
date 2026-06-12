---
title: "Dialer configuration for ADSL2+ bridged modem fails."
date: 2011-07-17
forum: New to Ubuntu
---

### Post by melrokz on 2011-07-17
I tried to configure a dialer for my ADSL modem which is in bridged mode, using the DSL tab.
For a while, it worked well.
When I tried to connect from a desktop user account, it shows 'device not managed'
Please help me at the earliest, I need to use the Internet.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/811532](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/811532)

---

### Post by melrokz on 2011-07-24
```
 sudo service network-manager restart 
```

Solved. I just had to restart Network Manager! I guess it happened because the modem was down while Ubuntu was trying to automatically dial... just a wild guess ;)

---

### Post by melrokz on 2011-08-04
I think I should reopen this thread...

...with some more info on the issue. 
The broadband link to my ISP, BSNL, is not stable. It fails often and when it does so, the dialer in Win XP shows me
> Link to BSNL failed
Looks like this is the time when Network Manager in Ubuntu shows
> device not managed
I had to restart the Network Manager service to get back my connection. So maybe I need to reopen the bug in Launchpad?

Please post if you have a solution...

---

### Post by melrokz on 2011-08-04
This is my syslog of the incident:

> Aug  4 19:00:14 melvin-desktop pppd[1790]: No response to 3 echo-requests
Aug  4 19:00:14 melvin-desktop pppd[1790]: Serial link appears to be disconnected.
Aug  4 19:00:14 melvin-desktop pppd[1790]: Connect time 3.4 minutes.
Aug  4 19:00:14 melvin-desktop pppd[1790]: Sent 93821 bytes, received 1454207 bytes.
Aug  4 19:00:14 melvin-desktop pppd[1790]: Connection terminated.
Aug  4 19:00:14 melvin-desktop NetworkManager[654]: <info> (eth0): device state change: 8 -> 9 (reason 13)
Aug  4 19:00:14 melvin-desktop NetworkManager[654]: <warn> Activation (eth0) failed.
Aug  4 19:00:15 melvin-desktop NetworkManager[654]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> (eth0): now unmanaged
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> (eth0): device state change: 9 -> 1 (reason 36)
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> (eth0): deactivating device (reason: 36).
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <warn> could not read ppp stats: No such device
Aug  4 19:00:15 melvin-desktop pppd[1790]: Terminating on signal 15
Aug  4 19:00:15 melvin-desktop pppd[1790]: Exit.
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> (eth0): cleaning up...
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> (eth0): taking down device.
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug  4 19:00:15 melvin-desktop NetworkManager[654]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

---

### Post by dineshs on 2011-08-05
> The broadband link to my ISP, BSNL, is not stableYou mean your DSL lamp is not lighting then?> device not managed Can you post what is in /etc/network/interfaces?```
cat /etc/network/interfaces
```

---

### Post by kenneth celius on 2011-12-07
"looking dialer product for my mobile"'mysalesdialer'This is mobile based dialer works on both telephony and telephony. no tension of modem as well as law.

---

