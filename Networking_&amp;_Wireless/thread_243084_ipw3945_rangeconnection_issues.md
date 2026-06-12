---
title: "ipw3945 range/connection issues"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by SimonJW on 2006-08-24
Hi there, I hope someone can help me.

My inbuilt card in a brand new Dell D820 (chipset apparently ipw3945) has some issues connecting to a wireless network. My house has two AP's, one an "extender" to the other. WHen in the room with the extender, the computer is VERY fussy about what position it is in before it connects - I have to wander around the area before it will connect. It cannot even see the AP, let alone connect to it, unless you are in exactly the right place.

Once connected, however, there is abolsutely NO PROBLEM with moving to anywhere in the room, and the connection DOESN'T drop even if you stay in a position in which the laptop couldn't previously detect an AP. **iwconfig** reports a signal strength of 80%.

Windows XP will connect to the network in this room of my house from any place or position more or less immediately. This leads me to believe that the problem isn't with the card or the Access Points, but with the setup of the linux driver.

This problem occurs no matter what method I try to connect: NetworkManager (my preferred option), manual with **iwconfig**, the GUI tool supplied with Ubuntu, or **WiFi-Radar** from the universe repositories.

Please help if you can! Thank you

Some info from when it is connected:
Ubuntu Dapper LTS
Dell Latitude D820
Intel Core Duo Wireless (ipw3945) 
```
simon@simon-laptop:~$ modinfo ipw3945
filename:       /lib/modules/2.6.15-26-686/kernel/drivers/net/wireless/ipw3945/ipw3945.ko
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
version:        1.0.5m
author:         Copyright(c) 2003-2006 Intel Corporation
license:        GPL
vermagic:       2.6.15-26-686 SMP preempt 686 gcc-4.0
depends:        ieee80211
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
srcversion:     9CC0391C54861289B605F3C
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
simon@simon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"belkin54g"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:30:BD:9B:F7:2E
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-26 dBm  Noise level=-32 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:174   Missed beacon:0

sit0      no wireless extensions.

```

---

