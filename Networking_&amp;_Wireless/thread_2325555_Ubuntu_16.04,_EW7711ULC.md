---
title: "Ubuntu 16.04, EW7711ULC"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by oracle-phoenix on 2016-05-23
When I am new to linux, and Ubuntu.&nbsp; I love it!. I just have  one issue. I purchased an Edimax EW7711ULC, downloaded the linux drivers  from Edimax and I tried to make the drivers but run into a __DATE__  error. So I download the mt7620U drivers form MediaTek, and i tried to  make the drivers but run into __DATE__ error. After googling for what  seemed months i found [chenhai  github for the driver]("https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916&quot; data-cke-saved-href=&quot;https://github.com/chenhaiq/mt7610u_wifi_sta_v3002_dpo_20130916") and [sanrath  bitBucket for the driver]("https://bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit"), they both make and install fine. I  can see the wireless device in me network list but it says not manged or  disconnected. In terminal I typed ifconfig, and iwconfig and got this: 

```

:~$ ifconfig
enp3s0    Link encap:Ethernet  HWaddr d8:50:e6:3f:b7:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:791604 (791.6 KB)  TX bytes:791604 (791.6 KB)

ra0       Link encap:Ethernet  HWaddr 74:da:38:5d:79:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13978 (13.9 KB)  TX bytes:41184 (41.1 KB)

wlx74da3859c9f9 Link encap:Ethernet  HWaddr 74:da:38:59:c9:f9  
          inet addr:192.168.1.217  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d1e7:2711:86f1:3542/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15724247 (15.7 MB)  TX bytes:3983843 (3.9 MB)

```

and if I do iwconfig 

```

:~$ iwconfig
enp3s0    no wireless extensions.

wlx74da3859c9f9  IEEE 802.11bgn  ESSID:"Home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:A7:0A:B5:F8:54   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31   Missed beacon:0

ra0       Ralink STA  ESSID:""  Nickname:"MT7610U_STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

```

and I ghanged interface manged=true but still no dice.

What I need help with is to get his card to start up, and also to connect to my network. Thank you for any support or help in this matter.

---

### Post by QDR06VV9 on 2016-05-23
See this thread and look at what was posted by chili555
[http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244)

---

### Post by oracle-phoenix on 2016-05-23
Hi Runrickus, 
        Ironically, that is one of the threads I read up on, before posting my own. Are you recommending I download the drivers [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909") says to download?

---

### Post by praseodym on 2016-05-23
Why not installing the package [http://packages.ubuntu.com/xenial/rtl8812au-dkms](http://packages.ubuntu.com/xenial/rtl8812au-dkms)

---

### Post by QDR06VV9 on 2016-05-23
Well there is successful out comes from that post.
chili555 is well known for this kind of expertise.

---

### Post by oracle-phoenix on 2016-05-23
runrickus: I followed it and still in the same boat, I am starting to think this USB card is cursed.

praseodym: I just installed it, and it only recognises, and connect to the other USB card only.

---

