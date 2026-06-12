---
title: "wireless woes"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by strider1066 on 2008-06-14
After two weeks of poking at it with a sharp stick I can't figure out my wireless (a 2WIRE router/modem) problem. After running the below script both the KWiFiManager and iwconfig shows that my card is working. However, a ping fails. My main card is a bmc4318, but the result is the same with a Linksys pci card.

I've managed to get wireless working on another laptop under Kubuntu versions of Gutsy and Feisty but  now that I'm running Hardy....

```
#!/bin/bash
iwconfig wlan0 essid "2WIRE178"
iwconfig wlan0 mode managed
iwconfig wlan0 channel auto
iwconfig wlan0 rate 54M auto
iwconfig wlan0 key open s:"1234567890"
iwconfig wlan0 ap 00:ab:cd:ef:12:34
iwconfig wlan0 retry 7

iwconfig wlan0
ping -I wlan0 -c 5 google.com


steve@poohsPlace:~$ sudo ./startWireless
[sudo] password for steve:

<output>

wlan0     IEEE 802.11g  ESSID:"2WIRE178"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:ab:cd:ef:12:34
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:****-****-****-****-****
          Link Quality=75/100  Signal level=-39 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

PING google.com (72.14.207.99) from 192.168.1.66 wlan0: 56(84) bytes of data.
From poohs (192.168.1.66) icmp_seq=1 Destination Host Unreachable
From poohs (192.168.1.66) icmp_seq=2 Destination Host Unreachable
From poohs (192.168.1.66) icmp_seq=3 Destination Host Unreachable
From poohs (192.168.1.66) icmp_seq=4 Destination Host Unreachable
From poohs (192.168.1.66) icmp_seq=5 Destination Host Unreachable

--- google.com ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4045ms, pipe 3
```

Any thought would be appreciated.

---

### Post by superprash2003 on 2008-06-14
are you able to ping your wifi router properly?

---

### Post by prshah on 2008-06-14
> **strider1066 said:**
> 
steve@poohsPlace:~$ sudo ./startWireless
[sudo] password for steve:

<output>

wlan0     IEEE 802.11g  ESSID:"2WIRE178"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:ab:cd:ef:12:34
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:****-****-****-****-****
          Link Quality=75/100  Signal level=-39 dBm  Noise level=-71 dBm
[/CODE]




Can you post the output of ```
ifconfig wlan0
``` after running your script? Does ```
sudo /etc/init.d/networking restart
``` make any difference?

---

### Post by strider1066 on 2008-06-14
hi, I'm not sure how to ping my wifi router. I tried:
     **~$ ping -I wlan0 -b 192.168.1.255**
being the router's broadcast address and got:
[B]     --- 192.168.1.255 ping statistics ---
299 packets transmitted, 0 received, 100% packet loss, time 298095ms
[/B]

---

### Post by strider1066 on 2008-06-14
After the *restart *here is the recent iwconfig wlan0
[B]wlan0     IEEE 802.11g  ESSID:"2WIRE173"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:B3:9F:5A:41
          Bit Rate=2 Mb/s   Tx-Power=27 dBm
          Retry limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:****.****.****.****
          Link Quality=61/100  Signal level=-53 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/B]
Thank you, steve

---

### Post by superprash2003 on 2008-06-14
i think you should try pinging 192.168.1.1 that would most probably be your router ip

---

### Post by prshah on 2008-06-15
> **strider1066 said:**
> hi, I'm not sure how to ping my wifi router. I tried:

As suggested by superprash, your router's ip is most likely 192.168.1.1, if the broadcast address is 192.168.1.255.

We need to know what address your wireless is taking. ```
ifconfig wlan0
``` will tell us that. Also, it's more than likely that your router address will be specified as a nameserver in "/etc/resolv.conf": why not take a look at that ```
cat /etc/resolv.conf
``` If these don't solve anything, please post back output of _both_ these commands.

---

