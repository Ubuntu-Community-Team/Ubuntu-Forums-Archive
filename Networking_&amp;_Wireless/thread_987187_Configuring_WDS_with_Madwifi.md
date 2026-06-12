---
title: "Configuring WDS with Madwifi"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by alexzip on 2008-11-19
Hi all, i need to join two network segments using two Atheros wireless cards (PCMCIA Proxim Orinoco and D-link DWL-G520) and Madwifi (madwifi-hal-0.10.5.6-r3861-20080903.tar.gz in Ubuntu 8.10) but it doesn´t work.
Information source: [COLOR="Blue"][/COLOR][http://madwifi-project.org/wiki/UserDocs/WDSBridge]("http://madwifi-project.org/wiki/UserDocs/WDSBridge")[COLOR="Blue"][/COLOR]
I did the following:
**_Computer 1_**
```
wlanconfig ath0 create wlandev wifi0 wlanmode ap    # Create an AP
brctl addbr br0                                     # Create a bridge
iwpriv ath0 mode 3                             # 1 = 802.11a, 2 = 802.11b, 3 = 802.11g  
iwconfig ath0 essid wds channel 1
iwpriv ath0 wds 1
ifconfig ath0 up                                    # Bring up the interface and next up to the bridge
brctl addif br0 ath0
ifconfig br0 10.0.0.1 netmask 255.255.255.0 up                        # Bring up the bridge
wlanconfig ath1 create wlandev wifi0 wlanmode wds   # Now create a station
iwpriv ath1 mode 3
iwconfig ath1 channel 3
iwpriv ath1 wds_add <MAC tarjeta Atheros del PC2>
iwpriv ath1 wds 1
ifconfig ath1 up
brctl addif br0 ath1
echo 1 > /proc/sys/net/ipv4/ip_forward
```

**_Computer 2_**
```
wlanconfig ath0 create wlandev wifi0 wlanmode ap    # Create an AP
brctl addbr br0                                     # Create a bridge
iwpriv ath0 mode 3                              # 1 = 802.11a, 2 = 802.11b, 3 = 802.11g
iwconfig ath0 essid wds channel 1
iwpriv ath0 wds 1
ifconfig ath0 up                                    # Bring up the interface and next up to the bridge
brctl addif br0 ath0
ifconfig br0 10.0.0.2 netmask 255.255.255.0 up                        # Bring up the bridge
wlanconfig ath1 create wlandev wifi0 wlanmode wds   # Now create a station
iwpriv ath1 mode 3
iwconfig ath1 channel 3
iwpriv ath1 wds_add <MAC tarjeta Atheros del PC1>
iwpriv ath1 wds 1
ifconfig ath1 up
brctl addif br0 ath1
echo 1 > /proc/sys/net/ipv4/ip_forward
```

On each computer a wired network card:
**_Computer 1_**
```
ifconfig eth0 10.0.0.3 netmask 255.255.255.0 up
route add default gw 10.0.0.1
```

**_Computer 2_**
```
ifconfig eth0 10.0.0.4 netmask 255.255.255.0 up
route add default gw 10.0.0.2
```

Test:
Ping doesn´t responds from Computer 1 to 10.0.0.2 or 10.0.0.4.
Ping doesn´t responds from Computer 2 to 10.0.0.1 or 10.0.0.3.
¿How can I know if the WDS bridge is well made and the wifi cards are linked?
Please, someone could help me.

This is the configuration i want.
[IMG]http://perso.wanadoo.es/nneoxito/images/link.JPG[/IMG]

---

