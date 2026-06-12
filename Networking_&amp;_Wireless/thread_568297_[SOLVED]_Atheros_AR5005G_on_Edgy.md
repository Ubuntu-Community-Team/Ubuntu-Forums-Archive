---
title: "[SOLVED] Atheros AR5005G on Edgy"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by merike on 2007-10-05
I'm once again trying to get wifi working.

At the moment iwconfig shows:
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

My kernel:
2.6.17-12-generic
Appropriate restricted modules is installed.

So the first thing would be to get it show up there. In the end I'd like to be able to connect to my WPA(TKIP) network.

Bear in mind that while I'm comfortable with cd, ls and few other simple commands I'm not familiar with everything else linux.

---

### Post by merike on 2007-10-05
After reboot with irqpoll option I see ath0! I'm also able to scan. I added my SSID to network settings with correct password, but I didn't get a connection.

Iwconfig now:
```
ath0      IEEE 802.11g  ESSID:"Mayfly"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-254 dBm  Noise level=-42 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Do I need something else for WPA? I can't ping even my router.

---

### Post by Lambert on 2007-10-05
Check this page. I'm not sure what version of network manager is on edgy but know it didn't support wpa at one point. So you will have to go the route with out it.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

You won't be able to ping until you see associated and an ip listed in that output.

---

### Post by merike on 2007-10-06
I got it to work by configuring interfaces after reading the sticky thread here (too bad I didn't before). However it would only allow one ssid so I commented that out and tried with network manager as described in WPAHowTo. It seems to work too, but during first minutes I had connect-disconnect cycle. However it seems to stay connected now. I'm impressed! And happy :).
I suppose last time I tried fixing wifi those topics weren't there yet.
Edit: tried KDE and installed network-manager for it but I got no icon. Nevertheless I'm connected. I'd still need icon, though.
Second edit: it appeared after a while.

---

