---
title: "ZD1211 BlueNext USB Device not connecting wireless"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by tomduffy on 2006-08-30
Has anybody successfully installed one of these wireless devices in Dapper. I have got wlan0  wireless network in networking using Ndiswrapper (Although it takes forever to open networking) Entered my SSID and 10 digit WEP.It then hangs for ages but even then will not connect to my BTHomeHub. I have connected using ethernet so Hub ok](*,)

---

### Post by tomduffy on 2006-08-31
At the advice of Networkguy in another thread I have run the following

lsusb
Bus 003 Device 002 ID 0ace:1215 ZyDAS
Bus 003 Device 001 ID 0000:0000
Bus 001 Device 001 ID 0000:0000
Bus 002 Device 001 ID 0000:0000

lwconfig
lo          no wireless extension

eth0        no wireless extension

Wlan0       Auto Access Point: 00:00:74:06:BF:D0
            Link quality:0 Signal level:0 Noise level:0
            RX invalid nwid:0 RX invalid crypt:0 RX invalid      frag:0 

Sit0        no wireless extension


lfconfig
lo          link encap:local loopback
            inet addr 127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX Packets:9 errors:0 dropped:0 overruns:0 frame:0
            TX Packets:9 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:472 (472.0 b) TX bytes:472 (472.0 b)

Wlan0
            link encap:Ethernet HWaddr 00:02:72:56:2C:7A
            inet6 addr: fe80::202:72ff:fe56:2c7a/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
            RX Packets:80 errors:0 dropped:0 overruns:0 frame:0
            TX Packets:1 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:4573 (4.4 KiB) TX bytes:342 (342.0 b)

Now, this might as well be in a foreign language to me, can anybody see what the problem might be. Any help would be appreciated:confused:

---

### Post by NetworkGuy on 2006-08-31
It appears from looking in the Wiki that the driver for this card may not quite work correctly.  However the Wiki also includes instructions for obtaining and installing the correct driver.  However the  direction are probably a little old and you may need to subsitute the latest version of the driver instead of the one it wants you to install.

Visit this site to view those directions.
[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211)

Let us know if you run into any problems.

---

