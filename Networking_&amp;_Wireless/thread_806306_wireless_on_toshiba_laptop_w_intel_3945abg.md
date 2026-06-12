---
title: "wireless on toshiba laptop w/ intel 3945abg"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Th3Professor on 2008-05-24
The Toshiba (satellite a205-s5855 model) laptop has this card:
Intel Corporation PRO/Wireless 3945ABG Network Connection

According to:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

...it's supported... right?

Apparently I need the "ipw3945" driver... how do I get it?

I'm running Ubuntu (Studio) 8.04.

System>Administration>Hardware Drivers
...that pulls up an empty window.

Is there a link to a howto for getting wireless working?
I've checked the stickies and haven't seen step-by-step instructions, or similar.

Thank you.

EDIT:
Update, okay it looks like I have the driver "iwl3945"...
"lshw -C network" gives me this:
```
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:[etc.]
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
```EDIT 2:
Since the laptop says the wireless card is using driver iwl3945 (although a thread in here says use ipw3945 drivder)... and since I came across a thread that mentioned some kind of "fix" for the iwl3945, I found this recommended command:
```
sudo apt-get install linux-backports-modules-hardy-generic
```...should I do that or just leave it as is? (I don't want to screw anything up.)

EDIT 3:
Here's some more...
```

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:[etc.]
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=81/100  Signal level=-92 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00[etc.]
```

---

