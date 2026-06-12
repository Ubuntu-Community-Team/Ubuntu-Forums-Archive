---
title: "3945ABG in Dell (XPS M1210) wireless issue"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Diabolis on 2008-09-07
Wireless is not working in that card. I have tried many possible solutions and now I'm really stuck. So I'll post all the information that I have gathered and see if someone can help.

The driver and the hardware:
```
dmesg | grep 3945
[  168.048153] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[  168.048236] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[  168.048623] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  168.110511] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  172.005764] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels

```

The card partially works, I know that because I can scan available networks:
```
 iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:19:E4:01:93:A9
                    ESSID:"c0ffe"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=85/100  Signal level=-48 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000005693c5181

```

So I tried this:
```
sudo iwconfig wlan0 essid c0ffe
sudo iwconfig wlan0 key open 2#########1
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

and the output was this:
```

There is already a pid file /var/run/dhclient.pid with pid 7039
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:5f:9e:6c
Sending on   LPF/wlan0/00:1b:77:5f:9e:6c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
[B]
iwconfig:[/B]
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"c0ffe"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E4:01:93:A9   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**ifconfig:**
```

eth0      Link encap:Ethernet  HWaddr 00:18:8b:da:01:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4463761 (4.2 MB)  TX bytes:488721 (477.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97700 (95.4 KB)  TX bytes:97700 (95.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:5f:9e:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:77:5f:9e:6c  
          inet addr:169.254.6.187  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-5F-9E-6C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**tail -f /var/log/kern.log**
```

Sep  7 18:06:53 monica-laptop kernel: [  817.184188] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  7 18:07:13 monica-laptop kernel: [  839.568349] wlan0: Initial auth_alg=0
Sep  7 18:07:13 monica-laptop kernel: [  839.568360] wlan0: authenticate with AP 00:19:e4:01:93:a9
Sep  7 18:07:13 monica-laptop kernel: [  839.568385] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  7 18:07:14 monica-laptop kernel: [  837.622920] wlan0: authenticate with AP 00:19:e4:01:93:a9
Sep  7 18:07:14 monica-laptop kernel: [  837.622957] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  7 18:07:14 monica-laptop kernel: [  837.821841] wlan0: authenticate with AP 00:19:e4:01:93:a9
Sep  7 18:07:14 monica-laptop kernel: [  837.821879] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  7 18:07:14 monica-laptop kernel: [  840.169022] wlan0: authentication with AP 00:19:e4:01:93:a9 timed out
Sep  7 18:07:14 monica-laptop kernel: [  840.169032] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

```

The kill switch (I don't know what is that) seems to be fine. I supposed that because the last line doesn't have a warning, hopefully I'm not wrong.
[B]sudo cat /var/log/messages | grep switch
[/B]
```

Sep  7 13:49:31 monica-laptop kernel: [    6.536916] SMP alternatives: switching to UP code
Sep  7 13:49:31 monica-laptop kernel: [    6.869409] SMP alternatives: switching to SMP code
Sep  7 14:59:33 monica-laptop kernel: [    6.225981] SMP alternatives: switching to UP code
Sep  7 14:59:33 monica-laptop kernel: [    6.542778] SMP alternatives: switching to SMP code
Sep  7 16:18:47 monica-laptop kernel: [    7.508490] SMP alternatives: switching to UP code
Sep  7 16:18:47 monica-laptop kernel: [    7.825165] SMP alternatives: switching to SMP code
Sep  7 16:59:41 monica-laptop kernel: [   14.062371] SMP alternatives: switching to UP code
Sep  7 16:59:41 monica-laptop kernel: [   14.379425] SMP alternatives: switching to SMP code
Sep  7 17:05:38 monica-laptop kernel: [    5.696553] SMP alternatives: switching to UP code
Sep  7 17:05:38 monica-laptop kernel: [    6.013490] SMP alternatives: switching to SMP code
Sep  7 17:19:51 monica-laptop kernel: [  882.181566] Kill switch must be turned off for wireless networking to work.
Sep  7 17:20:01 monica-laptop kernel: [  892.754355] Kill switch must be turned off for wireless networking to work.
Sep  7 17:26:47 monica-laptop kernel: [    5.617467] SMP alternatives: switching to UP code
Sep  7 17:26:47 monica-laptop kernel: [    5.934412] SMP alternatives: switching to SMP code
Sep  7 17:47:36 monica-laptop kernel: [ 1264.972188] SMP alternatives: switching to UP code
Sep  7 17:47:36 monica-laptop kernel: [    0.339092] SMP alternatives: switching to SMP code
Sep  7 17:56:04 monica-laptop kernel: [  149.840527] SMP alternatives: switching to UP code
Sep  7 17:56:04 monica-laptop kernel: [  150.157822] SMP alternatives: switching to SMP code

```

About the software, I have the latest:
```

Ubuntu 8.04 (Hardy Heron)
linux-backports-modules-hardy-generic version: 2.6.24.19.21
linux-restricted-modules-generic version: 2.6.24.19.21
```

I tried this fix, but it didn't work.
[URL="http://ubuntuforums.org/showpost.php?p=5666022&postcount=9"]
> i have the same card and I needed to add the file /etc/modprobe.d/iwl3945 with contents  if the file /etc/modprobe.d/ipw3945 exists, delete it. then reboot.
[/URL]

I tried to use [WICD]("http://wicd.sourceforge.net/"), but it failed too.

---

### Post by chili555 on 2008-09-07
If you do:```
sudo iwconfig wlan0
```does it show your correct WEP key? How many characters are in that key? 10 or 26, I hope.

---

### Post by Diabolis on 2008-09-07
Yeah, it shows the key:
```
**sudo iwconfig wlan0** 
wlan0     IEEE 802.11g  ESSID:"c0ffe"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E4:01:93:A9   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:2###-####-#1
          Power Management:off
          Link Quality=92/100  Signal level=-37 dBm  Noise level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

10 characters long, WEP hex

I just noticed that if I suspend and then awake the laptop it kind of connects, or at least something happens. The network monitor applet shows the green bar as if it were connected, but the status just switches quickly between **idle** and **receiving**. And now the output of ifconfig has changed, it has now a new interface called **wlan0:avahi**. I don't know from where the addresses it has come from. Those are out of the range that is allowed by my router.

```

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:18:8b:da:01:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:445577 (435.1 KB)  TX bytes:51254 (50.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98576 (96.2 KB)  TX bytes:98576 (96.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:5f:9e:6c  
          inet6 addr: fe80::21b:77ff:fe5f:9e6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25531 (24.9 KB)  TX bytes:16307 (15.9 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:77:5f:9e:6c  
          inet addr:169.254.38.212  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-5F-9E-6C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Also dmesg throws more output than before, looks like if it were duping:
```
**dmesg | grep 3945**
[   38.546921] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   38.546926] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   38.547112] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   38.613023] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   39.312004] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    1.118501] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[    1.118506] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[    1.118626] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[    1.182738] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[    1.253884] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels

```

I just tried to turn off the Wi-Fi Catcher (I don't know what is that) through the BIOS, of course it didn't work. Took the idea from here:
[http://ubuntuforums.org/showpost.php?p=5158330&postcount=10](http://ubuntuforums.org/showpost.php?p=5158330&postcount=10)

---

