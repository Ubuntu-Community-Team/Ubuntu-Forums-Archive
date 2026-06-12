---
title: "Broadcom 4311 doesn't work in Edgy"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by Gustavo Narea on 2006-12-09
Hello, everybody.

I've been trying to get my wifi working by following [this tutorial]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29") and everything worked great [until the seventh step]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-6d614c29580a2a14cec5fa52014380e98af72e45"):

```
gustavo@valencia:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  **ESSID:off/any**
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

I'm using Kubuntu Edgy and NdisWrapper-1.31 on a Dell Inspiron 6400 + Broadcom chipset 4311 (rev 1).

TIA.

Cheers!

PS: Just in case, [I also had troubles in Dapper]("http://ubuntuforums.org/showthread.php?t=281769").

---

### Post by Gustavo Narea on 2006-12-15
Any suggestion?

By the way, the Kubuntu's startup is taking more time than usual since I followed this howto. It also happened with Dapper, at the "Configuring network interfaces" stage.

Cheers.

---

### Post by StormGuy on 2006-12-15
Hmm...I seem to be having the same problem.  I've tried uninstalling and reinstalling the drivers and ndiswrapper several times.  No luck :(

---

### Post by StormGuy on 2006-12-15
My machine is a Gateway and I'm running Ubuntu Edgy and trying to use the same Broadcom 4311 card.

If I try to use the wifi-radar, it also spams my terminal with errors saying "eth1: error fetching interface information: Device not found
eth1    No such device"

---

### Post by treo600 on 2006-12-17
Het guys I tried the tutorial and it works
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice))

it didnt work the first time but after few trials it did

the first mistake i did was using ndiswrapper 1.29 i got invalid device with that so I had to start over with ndiswrapper 1.28

with that i got to step 7 and my card was showing as eth1
i googled it and i found this forum
[http://ubuntuforums.org/showthread.php?t=201902&page=4](http://ubuntuforums.org/showthread.php?t=201902&page=4)
in the iftab file i erased evething except for lo and wlan0
I rebooted and i run iwconfig and it was wlan0
then i went on with setp 7
good luck this thing was bugging me for 2 months
what a releif,

---

### Post by Gustavo Narea on 2007-01-20
It works! :guitar: 

Just upgrade ndiswrapper to version 1.34 and that's it!

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

