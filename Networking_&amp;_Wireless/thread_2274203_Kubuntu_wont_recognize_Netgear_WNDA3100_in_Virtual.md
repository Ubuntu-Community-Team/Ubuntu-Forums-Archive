---
title: "Kubuntu wont recognize Netgear WNDA3100 in Virtualbox"
date: 2015-04-18
forum: Networking &amp; Wireless
---

### Post by adhd2 on 2015-04-18
Hello, first post of many i hope!
So iv created a virtualbox with Kubuntu. Everythings been going well, created an awesome desktop. I downloaded wine to read my install software (that i downloaded) and everything was going smooth untill it said "please insert Wireless USB now". I inserted it, and nothing. it doesn't act like it is plugged in. I even went to "my computer- devices" on Kubuntu, and it does not appear. I have been messing with this for 2 days now, and i think its time i get some help. Please, help.

---

### Post by adhd2 on 2015-04-18
I would really appreciate help on this. im currently web browsing for similar problems but can not find one that is actually, similar.

---

### Post by chili555 on 2015-04-18
Please search this forum for WDNA3100. See all the tear-stained 150 reply threads. If you still wish to proceed, follow the directions there.

There are many threads here about fully supported devices that plug and play.

EDIT: [http://ubuntuforums.org/showthread.php?t=2052594](http://ubuntuforums.org/showthread.php?t=2052594)

---

### Post by adhd2 on 2015-04-18
Thank you very much i shall try this now and update this page later!

---

### Post by adhd2 on 2015-04-18
Ok i looked and tried many things but nothing has worked.

this is what im seeing.....


seph@Seph:~$ lsusb
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
seph@Seph:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

seph@Seph:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:73:49:44  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe73:4944/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97059497 (97.0 MB)  TX bytes:61065281 (61.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:708928 (708.9 KB)  TX bytes:708928 (708.9 KB)

seph@Seph:~$

---

### Post by chili555 on 2015-04-18
I am inexperienced with Virtual Box but it appears that you correctly have the virtual ethernet bridged to the host machine's actual networking interface.

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

If you need more guidance as to networking in a virtual environment, I am not the best resource.

---

### Post by adhd2 on 2015-04-19
ah ok, thankyou anyways though. I still cant seem to get this to work. iv tried almost everything.

---

### Post by chili555 on 2015-04-19
What do these report?```
ndiswrapper -l
dmesg | grep ndis
```That's a lower-case L in the first command and the pipe symbol | in the second.

---

