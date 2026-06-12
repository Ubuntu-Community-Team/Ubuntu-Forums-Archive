---
title: "No APs detected using Acer C110, Intel 2100 &amp; Ubuntu 7.04"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by Sally_Dog on 2008-10-29
I'm running an Acer C110 Tablet PC with an Intel Wireless Pro 2100 on Ubuntu 7.04.

lshw       shows "command not found"

ifconfig   shows that eth1 exists but with no packets

lspci      shows "02:05.0 Network Controller: Intel Corporation Pro/Wireless LAN 2100 3B Mini PCI Adapter (rec 04)

iwconfig  shows 
          (unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point:
          Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid 
          frag:0
          Tx excessive retries:0  Invalid misc:0   Missed 
          beacon:0


iwlist      shows    eth1  No scan results


cat /sys/class/net/*/device/rf_kill  shows "2"


dmesg       shows eth1: Radio is disabled by RF switch


In the end I think I'm not detecting any access points because the power to my radio may be off.  This is confusing however, as the red icon to the right of the LCD screen signals that it is on.   Sadly, I'm frustrated and confused.

[COLOR="Blue"]Could someone please help - perhaps who has experience dealing with either WLAN C100/C110 issues before.  Many Thanks![/COLOR]

---

