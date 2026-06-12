---
title: "Ubuntu 18.04 fresh install - VPN &quot;Activation of network connection failed&quot;"
date: 2018-09-24
forum: Networking &amp; Wireless
---

### Post by andydrew23 on 2018-09-24
I have a fresh install of Ubuntu 18.04 and am trying to connect to my VPN. I have an openvpn config that works on other Ubuntu 18.04 machines that I imported. When I turn VPN on it immediately shuts off and I get a notification "Activation of network connection failed." I updated to the latest kernel and am still receiving the same error. /var/log/syslog and dmesg are both spammed with

[ 1110.423994] pcieport 0000:00:1c.0: AER: Corrected error received: 0000:00:1c.0
[ 1110.424034] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
[ 1110.424044] pcieport 0000:00:1c.0:   device [8086:9d14] error status/mask=00003000/00002000
[ 1110.424063] pcieport 0000:00:1c.0:    [12] Replay Timer Timeout 

Here is my pastebin output
[http://paste.ubuntu.com/p/p3FQQtvMnD/](http://paste.ubuntu.com/p/p3FQQtvMnD/)

---

