---
title: "eth0 is conected but idle and won't give me web access"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by net_vagabond on 2007-05-20
Hey guys, I just installed Ubuntu  6.06. I'm having  an issue where my computer seems to see my modem (comcast digital cable) but i says it's idle and I can't connect to the internet.my ifconfig information is below.
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:13:79:05
              inet6 addr: fe80::20f:1fff:fe13:7905/64 Scope:Link
              UP BROADCAST MULTICAST MTU:1500 Metric:1
               RX packets:1689 errors:1 dropped:1 overruns:0 frame:0
               TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqeuelen:1000
               RXbytes:117208 (114.4kiB)    TX bytes:5768 (5.6 KiB)
                Interrupt:177

I don't know what most of it means, just that it's important. I've tried pinging a google ip and some other stuff and none of the pings have worked. Any help that could be offered would be greatly appreciated.

---

### Post by waylow on 2007-05-20
is it a wired connection or wireless?

I also just installed (Feisty - nearly a week now) I had heaps of problems getting my wireless connected but it's connected now thanks to 
[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

I don't know much about linux yet but it looks like your machine isn't getting assigned a IP

if you post the output from this command somebody might be able to pick up the problem

```

cat /etc/network/interfaces

```

---

