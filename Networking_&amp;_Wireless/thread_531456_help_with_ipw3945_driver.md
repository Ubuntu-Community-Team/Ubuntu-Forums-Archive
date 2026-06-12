---
title: "help with ipw3945 driver"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by Bense on 2007-08-21
Hey guys, i'm having some difficulties here.  

First I was having problems with nm-applet connecting to the wireless networks, then it wasn't even picking up any networks at all.  I did some searching and installed wifi-radar.  It worked fine for about 30 minutes.  Then my connection flaked out.  

I tried to tinker some more but was unsucessful in my attempts and I saw something about how /var/run/dhclient.eth1.pid already existed.  I figured that nm-applet had some sort of lock on my card so I deleted both /var/run/dhclient.eth1.pid and /var/run/dhclient.eth2.pid

Still no luck so i rebooted.

Now when I try to run /etc/init.d/networking start

I receive
eth1: ERROR while getting interface flags: No such device

and
eth2: ERROR while getting interface flags: No such device

as well as
ath0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134812041
SIOCSIFADDR: No such device

but here's the thing, when I do an 

root@ (~) ls mod | grep ipw
ipw3945        119712   1
ieee80211       35656    1  ipw3945 

as well as lspci | grep 3945
06:00.0 Network controller.....


**AHAHAHAHA OMG I am the biggest idiot, I just realized that there was a switch on the right side of my laptop that turns WLAN off!  I just switched it into the on position and everything works!!!!**

I just got pwned

welp i don't feel like erasing this so if you guys ever run into this error learn from my mistakes

---

### Post by nosrednaekim on 2007-08-21
lol.... same thing happened to me once, almost filed a bug report :)

don't worry, we are ALL idots at one time or another.

---

