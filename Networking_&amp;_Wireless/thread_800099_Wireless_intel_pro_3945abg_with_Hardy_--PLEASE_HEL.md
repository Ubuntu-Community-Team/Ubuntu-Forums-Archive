---
title: "Wireless intel pro 3945abg with Hardy --PLEASE HELP, PLease"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by harryman01 on 2008-05-19
hello all

I have a little problem with 8.04, I  have a Toshiba Equium a110-252, which have a Intel Pro wireless 3945abg card, it was working with Ubuntu 7.10, and I did the upgrade to 8.04, and now stop working, I di also the update to the network manager.

so far I notice that I got a new interface called wmaster0, but I still got the eth1 which is my wireless

wmaster0  Link encap:UNSPEC  HWaddr 00-XX-XX-XX-XX-XX-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 00:13:02:b0:6d:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3164 (3.0 KB)  TX bytes:16298 (15.9 KB)

my iwconfig output is

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XXXXXX"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


also I notice that the network setting in gnome is not listing any available AP

can anyone please, provide me some guidance to fix this issue?

Thanks

---

### Post by harryman01 on 2008-05-19
> **harryman01 said:**
> hello all

I have a little problem with 8.04, I  have a Toshiba Equium a110-252, which have a Intel Pro wireless 3945abg card, it was working with Ubuntu 7.10, and I did the upgrade to 8.04, and now stop working, I di also the update to the network manager.

Thanks

also the  lshw -C network output is

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:b0:6d:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


thanks

---

### Post by harryman01 on 2008-05-20
any help please

---

### Post by chili555 on 2008-05-20
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```

After I installed this, mine works perfectly.

---

### Post by harryman01 on 2008-05-20
I will try it and, will let you know

Thansks

---

### Post by harryman01 on 2008-05-20
I tried sudo apt-get install linux-backports-modules-hardy-generic,but is not working, 

Any help please

---

### Post by harryman01 on 2008-05-20
I also try install wicd, and no luck

any aideas?

---

### Post by chili555 on 2008-05-20
> but is not workingCan you be a bit more specific? Is apt-get not working? Is your wireless card not working? Or, more likely, is Network Manager being lazy? When I see an interface with Received bytes and Transmit bytes:```
eth1 Link encap:Ethernet HWaddr 00:13:02:b0:6d:3b
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:28 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3164 (3.0 KB) TX bytes:16298 (15.9 KB)
```It sure looks like it is healty and trying to connect.

Are your encryption details, WEP, WPA, etc., double-checked and correct?

---

### Post by harryman01 on 2008-05-20
> **chili555 said:**
> Can you be a bit more specific? Is apt-get not working? Is your wireless card not working? Or, more likely, is Network Manager being lazy? When I see an interface with Received bytes and Transmit bytes:```
eth1 Link encap:Ethernet HWaddr 00:13:02:b0:6d:3b
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:28 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3164 (3.0 KB) TX bytes:16298 (15.9 KB)
```It sure looks like it is healty and trying to connect.

Are your encryption details, WEP, WPA, etc., double-checked and correct?

:) 

the wireless, :) still not working , I did tried everything, i also check the WPA key, the same, is I got no response

I also notice that the PC turns quite slow when is trying to connect, 

I also can confirm that when I use Wicd, I only can see my AP, do not connect

---

