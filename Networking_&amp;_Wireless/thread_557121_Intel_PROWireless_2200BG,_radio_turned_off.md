---
title: "Intel PRO/Wireless 2200BG, radio turned off"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by Azguz Bloodfist on 2007-09-22
Hello. I think I've broken my wireless configuration while trying to connect to a wireless network in my new house. The radio seems to be off and I can't turn it back on. I'm running duel boot with windows and I think the wireless on windows is broken too.

I don't have a clue what to do, but I hope there is enought info below to piece together a solution.


```
`--> sudo iwconfig eth1 txpower on                            07-09-22 13:07:20
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.
```

```
`--> sudo iwconfig eth1                                       07-09-22 13:07:26
eth1      radio off  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
`--> sudo ifconfig eth1                                       07-09-22 13:08:11
eth1      Link encap:Ethernet  HWaddr 00:0E:35:B0:74:2F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000 Memory:d0208000-d0208fff
```

```
`--> sudo lshw -C network                                     07-09-22 13:09:51
  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:70:de:e8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:d0204000-d0205fff irq:6
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:b0:74:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: iomemory:d0208000-d0208fff irq:10
```

```
`--> dmesg | grep wireless                                    07-09-22 13:10:06
[   26.108000] Kill switch must be turned off for wireless networking to work.
```

```
`--> iwpriv                                                   07-09-22 13:11:04
lo        no private ioctls.

eth0      no private ioctls.

eth1      Available private ioctls :
          set_power        (8BE0) : set   1 int   & get   0
          get_power        (8BE1) : set   0       & get  80 char
          set_mode         (8BE2) : set   1 int   & get   0
          get_mode         (8BE3) : set   0       & get  80 char
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get  16 char
          reset            (8BE6) : set   0 int   & get   0
          sw_reset         (8BE7) : set   0 int   & get   0
          monitor          (8BE8) : set   2 int   & get   0

ppp0      no private ioctls.
```

Thanks

Azguz

---

### Post by noob12 on 2007-09-22
Yes your radio is disabled.

What is the make and model of your laptop?

Most laptops will have (exactly) one of the following types of switching:
- Hardware slider switch located somewhere on the side or back of the laptop.
- FN+F2 or similar key combination with direct link to hardware
- Hotkey requiring a software driver.

Some laptops will also have a setting in the BIOS which needs to be enabled.

---

### Post by Azguz Bloodfist on 2007-09-23
Arrgh. I can't believe I was so stupid! There is a button on the front of my Acer Aspire 1680 that turns it on and off. I bit of googling found that out, but I believe it should light up (but doesn't on Ubuntu).

Thanks

---

### Post by noob12 on 2007-09-23
OK.  I don't know about the 1680 and it's not listed on the rfswitch laptop support matrix.  But judging by others of the same vintage:

[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

you will need to load the acerhk module and will need to toggle the procfs control file.  See the link for info about the 1640 and 1690.  My guess is yours will behave like one of those.

A recent version of the acerhk module is included in Ubuntu Feisty.  If you run 64-bit, use the acer_acpi module.

Users have reported getting things working this way in similar situations with the 2.6.20-16-generic kernel.  Not sure about earlier versions.

---

### Post by Azguz Bloodfist on 2007-09-25
There is a very subtle button/LED on the front that I pressed and it works now.

Thanks

---

