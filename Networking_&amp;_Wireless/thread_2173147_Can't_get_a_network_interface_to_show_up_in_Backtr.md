---
title: "Can't get a network interface to show up in Backtrack 5 R3"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by muckijeste on 2013-09-08
Hello all;

first of all I'd like to say I'm a newbie to Linux. I've used it for some time but never really got around at troubleshooting problems.

So I've installed Backtrack 5 R3 onto my hard disk and I'm using it side-by-side with my Windows 7. However, I can't seem to get an internet connection-most people say that this is because I didn't activate the networking. Yes, I have activated the networking by using the start networking command, however the only output I get is something like: "stop networking/waiting". There are no wireless connections in wicd and I can't get connect to the Internet using an ethernet cable either. In fact, Backtrack doesn't detect those internet flags like "wlan0" and "eth0" at all. Since I'm new to Backtrack and Linux completely, I didn't know what information should I put here in order to get help. The "iwconfig" command reported:

lo - no wireless extensions

the "ifconfig" command reported information about the Local Loopback connection but there was no information about the ethernet/wireless connection. If you guys need anything else, I'll be glad to give it to you. Hope we solve the problem;

Cheers

---

### Post by zero2xiii on 2013-09-08
Hay,

> first of all I'd like to say I'm a newbie to Linux. I've used it for some time but never really got around at troubleshooting problems.

Then first of all do not use backtrack? It is NOT a linux distro for people that do not have very good linux understanding and skills. Most things are set up exactly like they are because of the nature of the OS (used for pentesting, not browsing facebook) such as not network connectivity from the get go so you can be "silent" on the network. I would recommend over all to get a "normal" user distro like ubuntu or variant and use that instead.

Secondly, this forum is the wrong place if you really wish to stick to back track, there are a few dedicated pentesting forums around that use BT as its main OS.

Thirdly, if you really wish to continue here your quest:
```
lshw -c network
cat /etc/network/interfaces
lsmod
```

and then we can try and help you.

Not meaning to sound harsh in the above, but some distros are not meant to be used by people who do not know exactly what they are working with and how to use it.

Cheers

---

### Post by muckijeste on 2013-09-11
You're right; BackTrack is definitely for advanced users. I'll stick with Ubuntu 12.04 from now on. Thanks for your help/


Cheers

---

