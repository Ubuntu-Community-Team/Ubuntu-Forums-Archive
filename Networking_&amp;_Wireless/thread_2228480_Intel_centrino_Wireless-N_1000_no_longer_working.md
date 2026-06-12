---
title: "Intel centrino Wireless-N 1000 no longer working"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by guzella on 2014-06-07
Dear all,
since a kernel update (I suspect) my wireless is extremely slow and only works ocasionally with my home router.

This problem does not occur with some other public wireless (e.g. in the   library) and it vanishes completely when using a VPN client (cisco   anyconnect) in my home network. I cannot check whether it also concernes  the wired  connection as I hardly ever used it and it did not work  properly  previously.

Reducing the MTU did not reveal any improvement, I tried disabeling 11n   (in modprobe.d--> options iwlwifi 11n_disable=1--> using 0 does   not help) and eventually removing all the (obviously) unnecessary files  in modprobe.d.

I am using Kernel 3.2.0-64-generic under Ubuntu 12.04 (precise) 64-bit.
In the following outputs I did not realize any significant change when using the VPN client:

ifconfig wlan0 ```
Link encap:Ethernet  HWaddr 74:e5:0b:2c:22:c2  
          inet addr:192.162.2.222  Bcast:192.162.2.222  Mask:255.252.222.2
          inet6 addr: fe80::76e5:bff:fe2c:22c2/22 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53445043 (53.4 MB)  TX bytes:8613328 (8.6 MB)



```
(changed  some of the address numbers to make it anonymous)

iwconfig wlan0
```
IEEE 802.11bg  ESSID:"NAME"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 64:70:22:DD:2E:FC   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:456  Invalid misc:1887   Missed beacon:0

```
--> peculiarly high invlid misc

ls /etc/modprobe.d
```
alsa-base.conf               blacklist-watchdog.conf
blacklist-ath_pci.conf       dkms.conf
blacklist.conf               fglrx.conf
blacklist-firewire.conf      iwl-legacy.conf
blacklist-framebuffer.conf   iwlwifi-disable11n.conf
blacklist-modem.conf         iwlwifi-disable11n.conf~
blacklist-oss.conf           oss-compat.conf
blacklist-rare-network.conf  vmwgfx-fbdev.conf

```
--> are there some more to be removed?

[TABLE="class: result_table withquestions"]
[TR="class: row_first"]
[TD="class: sentence right2 warn"]I am tankful for all advice!
Marco[/TD]
[/TR]
[/TABLE]

---

### Post by guzella on 2014-06-09
Hello,
sorry for bumping this thread. 
Would switching the router to 5 GHz help? There are lots of other wifis in the 2.4 GHz range around. 
I  am sharing the wifi with a collegue who had previously had problems  using ubuntu but improved by switching to debian, now it is vice versa.  Might it be some interference?

Online speed test ([www.speed.io]("http://www.speed.io"))  give a download speed in the range of 0.5-1 Mb/s, upload of 200 Kb/s  pings of 40 ms and 500 connections/min when doing it repeatedly, however  loading these pages first takes ages. The first time it shows 0 Kb/s  download, 50 Kb/s upload, pings of 40 ms and 320 connections/min.
What does that mean?

Loading  the New York Times ([www.nytimes.com]("http://www.nytimes.com")) for instance takes 40 seconds  without VPN client and less then 2 seconds when using the cisco VPN  client.

Greetings
Marco

---

