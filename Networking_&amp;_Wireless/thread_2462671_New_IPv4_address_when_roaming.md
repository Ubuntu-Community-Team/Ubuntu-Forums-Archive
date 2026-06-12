---
title: "New IPv4 address when roaming"
date: 2021-05-25
forum: Networking &amp; Wireless
---

### Post by troffasky on 2021-05-25
Using arpwatch on my Debian router at home.
Since I upgraded my laptop to 21.04 I am getting multiple emails a day saying that my laptop MAC has a new IP. 
On investigation it looks like this is happening when my laptop roams between APs.
It doesn't affect IPv6 [which is a relief because I am pretty sure my SSH sessions would be dropping if my IP address is changing].

From the laptop:
```

May 25 12:27:19 lt07 NetworkManager[1030]: <info>  [1621942039.6774] dhcp4 (wlp8s0): state changed unknown -> bound, address=192.168.1.41
May 25 12:29:50 lt07 NetworkManager[1030]: <info>  [1621942190.5339] policy: set 'tester' (wlp8s0) as default for IPv6 routing and DNS
May 25 12:29:50 lt07 NetworkManager[1030]: <info>  [1621942190.5383] policy: set 'tester' (wlp8s0) as default for IPv6 routing and DNS
May 25 12:30:15 lt07 wpa_supplicant[1072]: wlp8s0: WPA: Group rekeying completed with 64:d1:54:b5:9f:2c [GTK=CCMP]
May 25 12:31:18 lt07 NetworkManager[1030]: <info>  [1621942278.3334] manager: NetworkManager state is now CONNECTED_SITE
May 25 12:31:18 lt07 NetworkManager[1030]: <info>  [1621942278.6315] manager: NetworkManager state is now CONNECTED_GLOBAL
May 25 12:33:39 lt07 wpa_supplicant[1072]: wlp8s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-78 noise=9999 txrate=21700
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: SME: Trying to authenticate with d4:ca:6d:e3:a0:ed (SSID='tester' freq=2452 MHz)
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6829] device (wlp8s0): supplicant interface state: completed -> authenticating
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6830] device (p2p-dev-wlp8s0): supplicant management interface state: completed -> authenticating
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6831] device (wlp8s0): DHCPv4 lease renewal requested
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6842] dhcp4 (wlp8s0): canceled DHCP transaction
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6842] dhcp4 (wlp8s0): state changed bound -> done
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6847] dhcp4 (wlp8s0): activation: beginning transaction (timeout in 45 seconds)
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: Trying to associate with d4:ca:6d:e3:a0:ed (SSID='tester' freq=2452 MHz)
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6859] device (wlp8s0): supplicant interface state: authenticating -> associating
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.6860] device (p2p-dev-wlp8s0): supplicant management interface state: authenticating -> associating
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: Associated with d4:ca:6d:e3:a0:ed
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.7028] device (wlp8s0): supplicant interface state: associating -> 4way_handshake
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.7028] device (p2p-dev-wlp8s0): supplicant management interface state: associating -> 4way_handshake
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: WPA: Key negotiation completed with d4:ca:6d:e3:a0:ed [PTK=CCMP GTK=CCMP]
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: CTRL-EVENT-CONNECTED - Connection to d4:ca:6d:e3:a0:ed completed [id=0 id_str=]
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.7143] device (wlp8s0): supplicant interface state: 4way_handshake -> completed
May 25 12:34:12 lt07 NetworkManager[1030]: <info>  [1621942452.7147] device (p2p-dev-wlp8s0): supplicant management interface state: 4way_handshake -> completed
May 25 12:34:12 lt07 wpa_supplicant[1072]: wlp8s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-32 noise=9999 txrate=150000
May 25 12:34:18 lt07 NetworkManager[1030]: <info>  [1621942458.3955] dhcp4 (wlp8s0): state changed unknown -> bound, address=192.168.1.48

```

From the router:
```

May 25 12:27:19 togre dhcpd[2605979]: DHCPACK on 192.168.1.41 to d0:7e:35:3a:12:f4 (lt07) via br0
May 25 12:34:14 togre dhcpd[2605979]: DHCPDISCOVER from d0:7e:35:3a:12:f4 (lt07) via br0
May 25 12:34:17 togre dhcpd[2605979]: DHCPDISCOVER from d0:7e:35:3a:12:f4 via br0
May 25 12:34:18 togre dhcpd[2605979]: DHCPOFFER on 192.168.1.48 to d0:7e:35:3a:12:f4 (lt07) via br0
May 25 12:34:18 togre dhcpd[2605979]: DHCPREQUEST for 192.168.1.48 (192.168.1.3) from d0:7e:35:3a:12:f4 (lt07) via br0
May 25 12:34:18 togre dhcpd[2605979]: DHCPACK on 192.168.1.48 to d0:7e:35:3a:12:f4 (lt07) via br0
May 25 12:34:19 togre arpwatch[1192276]: changed ethernet address 192.168.1.48 d0:7e:35:3a:12:f4 (b8:d4:e7:30:4e:c0) br0

```

From this I can see that the client is sending two DHCPDISCOVERs 3s apart, maybe that explains why it gets a different v4 IP?
Also, the second one doesn't include a hostname. Don't know if that is significant

---

### Post by TheFu on 2021-05-25
If your router supports _DHCP reservations_, use those for the MAC in the laptop. Make the reserved IP outside the normal DHCP address range.

You can also tell the laptop wifi not to change APs automatically and there is a wifi NIC option to control how quickly it will change APs, if you want to screw around with that. I think it has to be added to the module loading line in /etc/modprobe.d/ . The exact option will be NIC and driver specific.

Because I don't know how to secure IPv6, I have it disabled on all my systems and my router blocked all attempts to tunnel IPv6 through IPv4 - thanks Microsoft.

---

### Post by slickymaster on 2021-05-25
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2021-05-26
If your wireless is roaming to another AP, then I would *expect *a different IPv4 address. The behavior is entirely correct.

What I would *not *expect is that a computer that needs to be always available by SSH would be allowed to roam. Frankly, I also wonder why a DHCP address would be allowed. D stands for dynamic; i.e. changing. 

At the least, I suggest that you bind your wireless to the preferred AP like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

