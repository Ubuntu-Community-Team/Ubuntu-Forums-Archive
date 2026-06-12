---
title: "Connection Slowing Down Then Dying"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by shaggy1054 on 2008-05-27
I recently downloaded a batch of updates using the manager utility. Immediately afterwards, my wireless performance went to hell. I get fast internet for a second or two on login, and then performance steadily degrades to the point where I am reconnecting every couple minutes just to stay on the internet. I'm using 8.04, and use the MadWifi .9.4 drivers. Here's the output when I run iwconfig: 

nate@caracol:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dd-wrt"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:10:10:00:03   
          Bit Rate:2 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-44 dBm  Noise level=-97 dBm
          Rx invalid nwid:10554  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.


I've tried running things with the two third-party drivers active and inactive (Atheros Hardware Access Layer and Support for Atheros 802.11 wireless LAN cards). No setting seems to help - the only thing that does is a reboot, but again, degradation occurs. Anyone have an idea as to what is going on here?

Thanks!

edit: I just checked to see what my wireless card was (for here) and I got this: 

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
        Subsystem: Lenovo ThinkPad T60
        Flags: bus master, fast devsel, latency 0, IRQ 217
        Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=32]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: IBM ThinkPad 11a/b/g Wireless LAN Mini Express Adapter (AR5BXB6)
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at edf00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---

### Post by quelx on 2008-06-06
I was having this problem with **dd-wrt** v24 and **iwl3945** (2.6.24-gentoo-r8 and ubuntu's 2.6.24-1{7,8}) it seems to be working once I changed the channel to **1**.  I didn't choose that channel before because someone else nearby was using it and well you know, interference and all that...  Windows on the same lappy wouldn't connect either. So maybe try some new channels and see how it goes.

---

