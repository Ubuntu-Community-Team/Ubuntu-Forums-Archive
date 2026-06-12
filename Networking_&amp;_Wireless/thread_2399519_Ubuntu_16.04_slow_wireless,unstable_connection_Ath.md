---
title: "Ubuntu 16.04 slow wireless,unstable connection Atheros AR9485"
date: 2018-08-26
forum: Networking &amp; Wireless
---

### Post by annaos on 2018-08-26
Ubuntu 16.04 slow wireless,unstable connection Atheros AR9485

I thought I would start a new thread on my particular problem with this wireless card. I have seen other problems but nothing have solved my problem. 

Recently I installed Ubuntu 16.04. Wireless connects and works just fine first minuts. Then it will be sometimes extrem slow. If I turn wireless off and then turn on, it will work some minutes good. It is extrem bad when I turn it back on after sleep mode. It is not a problem with the router or signal, my other devices connect fine. Earlier on this laptop I had Fedora and there was not such problem.

Thank you in advance for the help.

Running Ubuntu 16.04 on a Sony Vaio SVT1313V1ES
Output from lspci | grep Wireless

```

02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

```


Output from iwconfig:
```

veth6ec15ac  no wireless extensions.


docker0   no wireless extensions.


veth45390eb  no wireless extensions.


br-835a3802e15a  no wireless extensions.


lo        no wireless extensions.


enp14s0   no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:"unknown"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:49:79:8E:02:61   
          Bit Rate=40.5 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:477   Missed beacon:0


br-0457ba0d3f02  no wireless extensions.

```

Output from rfkill list all:
```
0: sony-wifi: Wireless LAN    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

cat ath9k.conf:

```
options ath9k nohwcrypt=1
```

Here is output of the wireless-script when internet is slow: [http://paste.ubuntu.com/p/KbVcbtknvT/](http://paste.ubuntu.com/p/KbVcbtknvT/)
Attached is output of wireless-script, when internet don't work anymore and I should restart wifi.

---

### Post by annaos on 2018-08-29
What me helped was country preferences:

```
[COLOR=#000000][FONT=&amp]sudo sed -i "s/REGDOMAIN=/REGDOMAIN=DE/g" /etc/default/crda [/FONT][/COLOR]
```

from [https://forum.ubuntuusers.de/topic/wlan-extrem-langsam-ubuntu-16-04/](https://forum.ubuntuusers.de/topic/wlan-extrem-langsam-ubuntu-16-04/)

---

