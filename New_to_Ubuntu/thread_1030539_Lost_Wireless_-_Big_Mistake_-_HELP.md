---
title: "Lost Wireless - Big Mistake - HELP"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-01-04
IAfter viewing other links re:Lost Wireless, I noticed someone else with the same wireless card had lost their connection. (see [http://ubuntuforums.org/showthread.php?t=1030416](http://ubuntuforums.org/showthread.php?t=1030416)) I made a major mistake by trying to adapt an Intrepid command to correct the problem in Hardy. I now have GStreamer problem... Any ideas on how to reverse my screw-up ???:confused:

---

### Post by northern lights on 2009-01-04
Could you state said "Intrepid command"?

Further, please post the outputs of ```
sudo lshw -C network
``````
iwconfig
```and```
ifconfig
```

---

### Post by jimmy the saint on 2009-01-04
was
> sudo apt-get install linux-backports-modules-intrepid-generic
the command you tried to adapt for hardy?

---

### Post by CoCoKnots on 2009-01-04
Hi Northern Lights..

This is what came back. Thanks.

cocoknots@cocoknots-laptop:~$ sudo lshw -C network
[sudo] password for cocoknots: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:09:c0:70
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:0a:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:47:2f:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


cocoknots@cocoknots-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cocoknots@cocoknots-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:47:2f:f8  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe47:2ff8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3088769 (2.9 MB)  TX bytes:526815 (514.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60100 (58.6 KB)  TX bytes:60100 (58.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:09:c0:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-09-C0-70-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

cocoknots@cocoknots-laptop:~$

---

### Post by CoCoKnots on 2009-01-04
Hi Jimmy the Saint,
Yes... I know now it was not a smart thing to do... It sounded right at the time.

---

### Post by CoCoKnots on 2009-01-04
When I go to Sys>Admin>SynPkgMgr How do I know which GStreamer files I need to reload ? Is there a package of files I need to go with that ?

---

### Post by northern lights on 2009-01-04
Your wireless device appears to be setup correctly. That's good news.

What does running ```
iwlist wmaster0 scanning
``` or ```
iwlist wlan0 scanning
``` yield? Find any networks?

---

### Post by CoCoKnots on 2009-01-04
cocoknots@cocoknots-laptop:~$ iwlist wmaster0 scanning
wmaster0  Interface doesn't support scanning.

cocoknots@cocoknots-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results

cocoknots@cocoknots-laptop:~$

---

### Post by CoCoKnots on 2009-01-04
Would it be better if I re-install 8.04 from scratch ?

---

### Post by CoCoKnots on 2009-01-04
I also loose control of the system. I cannot access Firefox or shut down without using the power button.

---

### Post by Guille Damke on 2009-01-04
Hi,

Try to do a copy of this file: /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bckup
```

And edit the first one, and comment everything (add "#" at the beginning of each line) except for:
```

auto lo
iface lo inet loopback

```

Probably, you'll have to reboot to apply changes. In the worst case, just move back your .bckup file back.
Good luck.

---

### Post by northern lights on 2009-01-04
> **CoCoKnots said:**
> Would it be better if I re-install 8.04 from scratch ?
I hate to give this as initial advice (as it sorta sucks if the first thing your told in a support forum is "go reinstall your system"), but, especially given this
> **CoCoKnots said:**
> I also loose control of the system. I cannot access Firefox or shut down without using the power button.
it might be the easiest.

Anyhow, it's late in mainland Europe and I've gotta get up early tomorrow morning. So good luck for now. I'll check back tomorrow.

---

