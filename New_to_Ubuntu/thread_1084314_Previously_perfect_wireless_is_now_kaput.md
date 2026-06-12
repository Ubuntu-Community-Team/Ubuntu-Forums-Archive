---
title: "Previously perfect wireless is now kaput"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by cc.chapman on 2009-03-01
I've been reading the forums looking for clues, but it seems that most people's wireless troubles were present since they installed Ubuntu.

Until last week, I was able to connect to my university's student wireless system through Network Manager.  I usually disable the wireless when I'm off campus to prevent it from trying to automatically connect to other wireless networks in my neighborhood.  Last Thursday, I tried to enable my wireless but the option is greyed out.  I am able to get online through ethernet, but it is not available on all areas of my campus.

I'm not sure if this is a driver problem since it was working fine until recently. I'm using Ubuntu 8.10, 64-bit version.  

Results of lspci (I'm just going to include what I think is relevant, but I have everything in a text document if I need to upload the entire results.):  
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Results of lshw -class network:
*-network               

       description: Ethernet interface

       product: 82566MM Gigabit Network Connection

       vendor: Intel Corporation

       physical id: 19

       bus info: pci@0000:00:19.0

       logical name: eth0

       version: 03

       serial: 00:1e:37:8e:74:cc

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 ip=10.253.56.88 latency=0 module=e1000e multicast=yes

  *-network DISABLED

       description: Wireless interface

       product: PRO/Wireless 3945ABG [Golan] Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:03:00.0

       logical name: wmaster0

       version: 02

       serial: 00:1c:bf:bc:fe:0b

       width: 32 bits

       clock: 33MHz

       capabilities: cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 4a:ff:79:a3:be:89

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Results of ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1e:37:8e:74:cc  

          inet addr:10.253.56.88  Bcast:10.253.56.255  Mask:255.255.255.0

          inet6 addr: fe80::21e:37ff:fe8e:74cc/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:28783 errors:0 dropped:0 overruns:0 frame:0

          TX packets:39658 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:100 

          RX bytes:23540357 (23.5 MB)  TX bytes:18172093 (18.1 MB)

          Memory:fe000000-fe020000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)


Results of iwconfig:
lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11abg  ESSID:""  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=0 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



pan0      no wireless extensions.

---

### Post by chrisod on 2009-03-01
Does your laptop have hardware switch to turn off wireless?

---

### Post by cc.chapman on 2009-03-01
A "hardware switch" as in a physical button on the exterior of my laptop?  In that case, I believe not, at least not that I've noticed in the past year and a half I've had this laptop.

---

### Post by chrisod on 2009-03-01
Yes, a physical switch or button. I once spent several hours troubleshooting dead wireless before I realized I had a physical switch that I must have accidentally set to off.

---

### Post by cc.chapman on 2009-03-01
I never noticed that tiny sliding switch on the front bottom of my laptop, near the headphones jack.  After I slid it over to the green side with the laptop in parenthesis icon and restarted the computer it of course worked.

I'm so sorry for wasting your time.  Although I did learn a lot about wireless networks the past couple of days.

---

