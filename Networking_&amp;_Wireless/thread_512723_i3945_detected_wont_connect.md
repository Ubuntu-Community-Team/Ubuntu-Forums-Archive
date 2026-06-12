---
title: "i3945 detected wont connect"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by pgmer6809 on 2007-07-29
HP Pavilion DV1000. Clean install of Feisty.  SMC barricade wireless. Wireless works under XP flawlessly. WEP key enabled.
Under Feisty i3945 is detected. Will show up in system->admin->network. I can set properties ssid, wep key etc. But I can never connect to the wireless. Wired LAN works ok most of the time.

lsmod shows the ieee80211 encrypt and encrypt_wep modules installed/loaded.
the syslog reports events when the rf kill switch on the DV1000 kbd is pressed.
They syslog reports that it has detected geography of the i3945 Ok. 
but no connection. 
I can run iwconfig and ifconfig and dhcpclient on the interface and they work OK. IP address gets assigned etc.
I also tried disabling security on the router temporarily to see if I could connect when there was no WEP involved, but no joy.
any suggestions that do NOT involve downloading and installing new pacakges?
Thanks,
pgmer6809
-------------------------------------------------------------------------------
[  279.596000] ipw3945: Radio Frequency Kill Switch is On:
[  279.596000] Kill switch must be turned off for wireless networking to work.
[  294.728000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a 
----------------------------------------------------------------------------------
greg@Pavillion-Ubuntu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:13:02:16:96:98  
          inet addr:192.168.2.139  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1531 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 Memory:d6000000-d6000fff 

---------------------------------------------------------------------------------------------------
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1566   Missed beacon:0

..........................above is with the kill switch failing to work. ......................
When kill switch works, above is different.

---

