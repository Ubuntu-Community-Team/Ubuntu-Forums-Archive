---
title: "Issues with  Intel PRO/Wireless 3945ABG"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by DarkWingedOmen on 2008-08-27
I everyone, i got a problem that's driving me crazy, i'm a total newbie in ubuntu, got a fresh install of ubuntu 8.04.1, everything worked just fine, except for my wireless card an Intel PRO/Wireless 3945ABG, i tried some of the solutions in this forum ( linux-backports-modules-hardy-generic) with no success, i got a Dell XPS m1530

Can anyone help me? this is what lshw -C network throw:

  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: ff:ff:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a


and iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

P.S.: strangely last night it worked but when i turned my notebook on today, nothing...

---

### Post by DarkWingedOmen on 2008-08-27
Some advice here would be very apreciated...

---

### Post by catabriga on 2008-08-27
Have you tried ndiswrapper? It usually solves most problems with wireless connection, just search in the forum, there are tons of tutorials and posts.

---

### Post by DarkWingedOmen on 2008-08-28
> **catabriga said:**
> Have you tried ndiswrapper? It usually solves most problems with wireless connection, just search in the forum, there are tons of tutorials and posts.
Is this ndiswrapper reversible? i mean, can i uninstall it or return to the previous driver if I'm not satisfied with it?

---

### Post by catabriga on 2008-08-28
Yes, its completely reversible, you should really try it.

For making things easier, there is a graphical interface fo ndiswrapper, search for ndisgtk in synaptic. You will need your drivers for windows, then just run ndisgtk and tell ndisgtk where the windows drivers are. It's going to set everything for you. If that doesn't work (probably will work) you can try to use ndiswrapper configuring yourself, just search some thread about it in the forum.

---

