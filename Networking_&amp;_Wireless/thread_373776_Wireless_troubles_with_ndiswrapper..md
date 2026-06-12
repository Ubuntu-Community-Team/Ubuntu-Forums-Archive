---
title: "Wireless troubles with ndiswrapper."
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by floyd27 on 2007-03-01
Hello.
I have been able to use ndiswrapper successfully in the past, but I have run into a problem with this wireless card.

It is a Dlink USB WUA2340.

I have ndiswrapper 1.38 installed with the latest windows drivers.
#####################
roderick@linuxbox:~$ ndiswrapper -l
neta5agu : driver installed
        device (07D1:3A08) present
roderick@linuxbox:~$
 
When I try to connect through the "kwifiassistant" I cannot get it to connect at all.

-I have the drivers installed
-Did modprobe ndiswrapper
-did depmod -a
-the card is recognized.

#######################

wifi0     Link encap:UNSPEC  HWaddr 00-14-78-73-CD-16-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:9922
          TX packets:2403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:3239 (3.1 KiB)  TX bytes:110538 (107.9 KiB)
          Interrupt:74 Memory:f8b80000-f8b90000

wlan0     Link encap:Ethernet  HWaddr 00:17:9A:0A:AD:41
          inet6 addr: fe80::217:9aff:fe0a:ad41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12835 (12.5 KiB)  TX bytes:5621 (5.4 KiB)

Is there a step im missing here?

Do I need to provide any more info to get this resolved?

Thank you for any advice..
:)

I just want to be able to use Linux again...Thats all I ask

---

### Post by floyd27 on 2007-03-01
BTW im running edgy eft 32 bit Kubuntu.

I have no way of accessing the net through linux.
I have to boot into windows to DL files and move them to a shared folder.

I have no done build essentials as I do not know how to get the files though windows..
thanks

---

### Post by spd106 on 2007-03-01
Are you able to scan for networks?

Through gui or iwlist wlan0 scan.

---

### Post by floyd27 on 2007-03-01
yes, I can scan the network and see my network id "semex"..
It reads the same connection strength as it does in windows.

Just when I try to connect it says "connection failed" over and over again.

Any ideas?

---

