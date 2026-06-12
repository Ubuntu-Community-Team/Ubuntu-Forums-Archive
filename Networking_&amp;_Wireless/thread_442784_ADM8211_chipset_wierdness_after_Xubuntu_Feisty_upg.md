---
title: "ADM8211 chipset wierdness after Xubuntu Feisty upgrade"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Durito on 2007-05-13
So, I upgrade to Xubuntu Feisty (well, erased and reinstalled, actually), and it rocks. Except my wireless card, which worked out of the box on Ubuntu Edgy, is wonky. It loads the right module for the chipset (adm8211), but doesn't seem to be 'on'. As far as I can't tell, it's not transmitting, and sometimes not receiving. Also, there doesn't seem to be a txpower value returned by iwconfig, as there was in Edgy. Also, it's now wlan0 instead of eth0, and there's this wierd wmaster logical device that shows up. Any ideas? Here's the device info. Notice that it doesn't seem to be getting a signal from the access points. And dhclient doesn't return a working lease after several tries.

> 
 *-network
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 0
       bus info: pci@05:00.0
       logical name: wmaster0
       version: 20
       serial: 00:04:e2:7f:d1:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=adm8211 latency=64 maxlatency=128 mingnt=64 multicast=yes wireless=IEEE 802.11b
       resources: ioport:1800-18ff iomemory:30000000-300003ff irq:11
wmaster0  IEEE 802.11b  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11b  ESSID:"joebar"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1212 (1.1 KiB)  TX bytes:1212 (1.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:04:E2:7F:D1:66  
          inet6 addr: fe80::204:e2ff:fe7f:d166/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:12410 (12.1 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-04-E2-7F-D1-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B3:41:62:D9
                    ESSID:"fah"
                    Mode:Master
                    Frequency:2.427 GHz
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:off
                    Extra:tsf=000000611fcaa334
          Cell 02 - Address: 00:16:B6:28:84:20
                    ESSID:"joebar"
                    Mode:Master
                    Frequency:2.462 GHz
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:off
                    Extra:tsf=00000005f3e87c3d



Thanks, all. I'm running Xubuntu Feisty on a Thinkpad 600e. Any theories would be greatly appreciated.

---

### Post by jrmwvu04 on 2007-05-19
I don't have any more information for you other than to say I loaded Xubuntu Feisty on my roommate's machine, which also has a adm8211 wireless card, and I get all the same things you're describing. The only way I was able to get wireless working for the time being was using ndiswrapper, and even that, he tells me, isn't going beautifully.

---

