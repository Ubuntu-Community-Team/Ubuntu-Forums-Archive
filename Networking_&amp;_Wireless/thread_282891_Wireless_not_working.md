---
title: "Wireless not working"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by Klaymen on 2006-10-23
FINALY i managed to get som drivers for my wirelsess card, and everything worked fine. I can see the network in wifi radar, and i can connect to it ok, but when i try starting the internet it wont work... WHen i use a wired connection (in the same router) it works fine... any ideas?

---

### Post by invalid on 2006-10-23
Are you activating your card when you plug it in?
```
sudo ifup eth1
```
(Replace 1 with the appropriate device number of course)

---

### Post by Klaymen on 2006-10-23
I had already activated it... as i said, i could see the wireless network and everything. It says: "interface wlan0 already configured"

---

### Post by NetworkGuy on 2006-10-23
When you do a ifconfig wlan0 from a terminal, what do you get back as a response?

Are you getting an IP address from the wireless router?

---

### Post by Klaymen on 2006-10-23
Link encap: Ethernet  HWaddr 00:40:05:C9:BD:10
UP BROADCAST MULTICAST  MTU:1500  Metric: 1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:11 Base address:0x1800

---

### Post by NetworkGuy on 2006-10-23
You are not getting an IP address from your wireless router.

Does your router have WEP/WPA turned on?

If so, you may be having an issue with getting the key's to match up.

Also, post the output of an iwconfig to verify you are actually connected to your wireless router.

---

### Post by Klaymen on 2006-10-23
I had no problems when i used the card with windows...

iwconfig:
lo: no wireless extensions

eth0: no wireless extensions


wlan0: IEEE802.11b+  ESSID:"STAC9BD10" Nickname:"acx v0.3.21"
Mode:Managed  Frequency:2.412 GHz Access Point: Not-Associated
Bit-rate:22 Mb/s Tx-Power=18 dBm Sensitivity=187/255
Retry min limit:7 RTS thr:off
Power Management:off
Link Quality:0/100 Signal level:62/100 Noise level:45/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0: no wireless extensions

---

### Post by Klaymen on 2006-10-24
Anybody? Please? Or i have to start using windows again :(

---

### Post by m00t on 2007-09-21
i think i'm having the exact same problem as klaymen but i'm a total n00b so any linux terminology is like Chinese to me please help with simple instructions i'm still learning

---

### Post by Klaymen on 2007-09-21
Well... i never got i working. Switched back to windows, and now i'm running OS X. :/

---

### Post by HokeyFry on 2007-09-21
try the howto in my sig

---

