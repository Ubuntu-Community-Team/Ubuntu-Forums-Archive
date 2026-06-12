---
title: "ipw3945 (Intel/PRO Wireless 3945ABG) slow downstream compared to windows"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by SundeepG on 2007-07-21
Hey guys, sorry for posting this same problem again, but all the other threads I checked didnt have any solution to them. I just recently installed Ubuntu 7.04 and am a complete newb to Linux. However, I seem to be getting this same problem that many ppl with this driver (ipw3945) are experiencing. When I boot to windows XP, I can get download speeds of 5.5mbps, with an upload of around 1.5mbps. However, when running in Linux, my downloads usually cap out around 40KB/s, with a speed test result of around 800-1200kbps downstream (jumps a lot), yet my upload speeds are fine at 1.5mbps upstream. As you can see, I am only experiencing problems in my downstream rate. I am running the latest stable version of the ipw3945 driver:

driverinfo:
sghuman@sghuman-laptop:~$ iwconfig eth1
eth1 IEEE 802.11b ESSID:"MSHOME"
Mode:Managed Frequency:2.437 GHz Access Point: 00:50:F2:72:C2:22
Bit Rate:11 Mb/s Tx-Power:15 dBm
Retry limit:15 RTS thrff Fragment thrff
Power Managementff
**Link Quality=79/100 Signal level=-55 dBm Noise level=-56 dBm**
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 **Invalid misc:10740** Missed beacon:0

sghuman@sghuman-laptop:~$ modinfo ipw3945
filename: /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license: GPL
author: Copyright(c) 2003-2006 Intel Corporation
version: 1.2.0mp
description: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion: 9B03103B15A8FE1824967C2
alias: pci:v00008086d00004227sv*sd*bc*sc*i*
alias: pci:v00008086d00004222sv*sd*bc*sc*i*
depends: ieee80211
vermagic: 2.6.20-16-generic SMP mod_unload 586
parm: antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm: disable:manually disable the radio (default 0 [radio on]) (int)
parm: associate:auto associate when scanning (default 0 off) (int)
parm: auto_create:auto create adhoc network (default 1 on) (int)
parm: led:enable led control (default 1 on)
(int)
parm: channel:channel to limit associate to (default 0 [ANY]) (int)
parm: rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm: mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)

Broadband Reports TweakTest Results:
[http://www.dslreports.com/tweakr/blo...x&vi](http://www.dslreports.com/tweakr/blo...x&vi) a=normal

I found other threads (non-Ubuntu) related to this problem, but with no solutions. Some of the facts they brought up was the signal strength only being 1dB higher than the noise floor in people who experienced this problem and the invalid misc # being really high. Can anyone help me out here?

I've tried disabling ipv6 but that only made my connection slower... **can someone please help me out, or at least tell me wut the deal is with the high invalid misc number - what it means and how do i fix it?**

Thanks

---

### Post by finite9 on 2007-07-21
i just noticed this problem today with my laptop.  4.9GB was going to take 1hr to transfer across a router to my other laptop.  I thought to heck with this, and connected both laptops via ethernet cable to the router, and it said 45mins!!!  I looked at System Monitor and it shows my netgraph spiking every second going to ~5Mbps to zero then back again.  This was with ethernet not wireless, so there is a problem here for sure.

---

### Post by SundeepG on 2007-07-21
yea i was going to try using ethernet and seeing if I still have the same problem, I'll get back to you on that... How is your upstream tho? My upload speeds seem to be totally unaffected, as I can get about 1.5mbps upstream (faster than my download speeds).

---

### Post by SundeepG on 2007-07-28
Hey sorry it took me so long to get back to you on this... I just tried doing a speed test after connecting with the ethernet port of my ipw3945 adapter (listed as eth0 for me).... I ended up getting 17.2 mbps down and 1.2 up... so my upload speed is the same either way, but there is definately a problem with my wireless. I tried moving my laptop right besides my wireless router and now I get these stats: 

sghuman@sghuman-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"MSHOME"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:F2:72:C2:22   
          Bit Rate:11 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          sghuman@sghuman-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"MSHOME"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:F2:72:C2:22   
          Bit Rate:11 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=98/100  Signal level=-27 dBm  Noise level=-28 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8185   Missed beacon:0

sghuman@sghuman-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:13:02:1A:4D:B2  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe1a:4db2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:8189 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9250422 (8.8 MiB)  TX bytes:4173469 (3.9 MiB)
          Interrupt:18 Base address:0x2000 Memory:54000000-54000fff 

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  **Invalid misc:8185**   Missed beacon:0

sghuman@sghuman-laptop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:13:02:1A:4D:B2  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe1a:4db2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 **dropped:8189** overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9250422 (8.8 MiB)  TX bytes:4173469 (3.9 MiB)
          Interrupt:18 Base address:0x2000 Memory:54000000-54000fff 

The problem definately lies in the signal strength/noise floor ratio, because now with my laptop right besides the router (stronger signal) i can get 3mbps downspeed. I think im having some kind of driver issue because my link quality is good but the signal strength is severely degraded but I have no problem with it when running Windows XP.

Can anyone help me out?

---

### Post by SundeepG on 2007-07-28
I managed to fix my problem by switching out my wireless routher from a Microsoft one I had to the Linksys WRT54GS router... I am not able to download as fast as I was connected through the ethernet port, although i still have the same signal/noise ratio , Rx dropped, and invalid misc stats.

---

### Post by finite9 on 2007-07-29
my issue turned out to be my misunderstanding, and a bit of a bug in Nautilus and System Monitor.  I was thinking that 100Mbit network meant 100 MegaBytes/sec.  It doesn't.  After converting all the figures, I realised that the 11.5MBytes/s I was getting through ethernet, was the max of a full duplex 100Mbit ethernet link more or less.

I tested download speed on wireless and it was 22Mbit/s, and the card supports 54Mbit/s, which is OK, as the 54Mbit standard in reality goes about 22Mbit/s.

The issue I had was that Nautilus in Ubuntu 7.04 takes 4 times longer than it should.  When I transferred the same file with SCP, then it took 10mins instead of 45mins.

Also, my system monitor spikes when transferring with ethernet, leading me to believe that this was the reason why speed was slow, but turns out this is a bug in system monitor.

I have not tested my wireless upload speed as of writing.  And ne thing that seemed strange was that when I connect two PCs with a crossover cable, my SCP transfer speeds doubled from 11Mbytes/s to 22MBytes/s.  I do not think this is the difference between half and full duplex, but I could be wrong....and think, or suspect that it is simply a unique quality of using a crossover cable...I still think I am getting full duplex when I go through my router but I am starting to have my suspicions....

If I upload a file via scp, that goes at 11.5MB/s, then I try to download a file from the server, it should go at full speed in both directions with full duplex, but it didn't...the downloading file went at exactly half the speed it should have done, but the uploading file stayed at 11.5MB/s...weird.

---

