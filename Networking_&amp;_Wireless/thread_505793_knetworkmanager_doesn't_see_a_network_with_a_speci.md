---
title: "knetworkmanager doesn't see a network with a special character on its ESSID"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by Mguel on 2007-07-20
Hi, using kubuntu 7.04 on a dell xps m1210. I haven't had problems with wireless networks and knetworkmanager until now that in my University they configured the wifi with the ESSID with a special character on it.

knetworkmanager simply doesn't see it.

I've tried to add it manually through the context menu of knetworkmanagar replacing the "í" character with normal "i", "?" or use "" or '' to enclose the name with no success. (used the "?" because with other notebook with WIFI Radar it recognized the network with a question mark instead of the special character).

Any help is appreciated, thank.

---

### Post by kevdog on 2007-07-20
What is your new ESSID with the special character?  Can you post it??

---

### Post by Mguel on 2007-07-23
> **kevdog said:**
> What is your new ESSID with the special character?  Can you post it??

Hi, yes... the ESSID is:

Facultad_Biología_U

where the special character is the "í" (accented i = &iacute; in html)

Cheers,
Mguel

---

### Post by Mguel on 2007-07-25
> **Mguel said:**
> Hi, yes... the ESSID is:

Facultad_Biología_U

where the special character is the "í" (accented i = &iacute; in html)

Cheers,
Mguel

I've installed wifi-radar, where I can confirm I see the network with the special character. After connecting, this is what I get doing a iwconfig: (**EDIT: See next post**)

```
eth1      IEEE 802.11g  ESSID:"default"  Nickname:"Facultad_Biolog&#65533;a_U"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:51:D6:C3
          Bit Rate:24 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/100  Signal level=-79 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0
```Previously with knetwork manager I saw a "default" network, but I believe it's not the same since it has a very low signal with very low speed while the one with the  special character is very fast. Now if I start knetworkmanager it shows that I'm connected to "default" but on the tooltip it displays two Access points, and previously it only showed one... maybe wifi-radar added the second one. And now the speed and signal is good.

I'm not sure about the interaction of wifi-radar with knetworkmanager, and if in the future knetworkmanager will automatically connect to the network correctly or if I will have to use wifi-radar every time I'm at the University.

Cheers

---

### Post by Mguel on 2007-07-27
Now I connected using the wifi-radar only (without starting knetworkmanager) and the iwconfig is: (now it displays the ESSID with the special character also and not only the nick)

```
eth1      IEEE 802.11g  ESSID:"Facultad_Biolog&#65533;a_U"  Nickname:"Facultad_Biolog&#65533;a_U"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:C7:99:F6:70
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-32 dBm  Noise level=-33 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0
```

---

