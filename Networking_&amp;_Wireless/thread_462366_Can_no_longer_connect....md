---
title: "Can no longer connect..."
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by tragicglee on 2007-06-02
I fixed it :oops: 

---

I'm completely clueless when it comes to wireless.

I'm running Dapper on an older Latitude. My card's a D-Link DWL-650G, and  my router is a [FON]("http://www.fon.com").  I'm currently unable to connect to either of my networks (MyPlace, which is WPA2 enabled, or FON_AP which is unsecured), though  I could do it in the past. I have not changed configs. This has been a persistent problem for the last few weeks but I haven't been sweating it because I've been able to go wired, but now, I need to be wireless full-time. I've been stuck in Windows for the last two days... my laptop's never felt so useless :P

I have network-manager-gnome installed. It used to list the networks, but it now says "no network devices have been found".  Network-Tools lists ath0 (which it's always shown as) as an unrecognized(?) device. Any idea where I should be looking or what I ought to try?

lspci does show the card...
0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

ifconfig outputs:
ath0   Link encap:Ethernet  HWaddr 00:80:C8:1F:78:DC
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:2052 (2.0 KiB)
          Interrupt:11 Memory:d0d00000-d0d10000

iwconfig outputs:
ath0   IEEE 802.11g  ESSID:"MyPlace"
         Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:84:14:92:0E
         Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
         Retry:off   RTS thr:off   Fragment thr:off
         Encryption key:0000-0000-00   Security mode:restricted
         Power Management:off
         Link Quality=73/94  Signal level=-22 dBm  Noise level=-95 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by MeeMaw on 2007-06-02
In the supported wireless card list, under Atheros 5212 it says;
"DAPPER: Nearly works out-of-the-box, but had to add "wireless-rate 11M" to /etc/network/interfaces + reboot."

Have you tried that? 

Good luck!!!!

---

### Post by tragicglee on 2007-06-02
Thanks for the suggestion, MeeMaw. I did add that line and do a reboot but there is no change.

---

