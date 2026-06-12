---
title: "wicd -1% signal strength."
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by RedTempo on 2008-03-21
I have 7.10 installed and I am using wicd to configure my wireless. With wicd I am using a D-Link wifi card and I ca connect to my network. The problem is I am getting -1% signal strength and cannot even connect to my router (localhost or 192.168.1.1) Please help:confused:

---

### Post by imdano on 2008-03-21
What's the output of iwconfig when you're connected?

---

### Post by RedTempo on 2008-03-22
I'm not sure. now ubuntu won't boot at all and the hard drive isn't even recognized by the motherboard. when I could boot into ubuntu the only thing that would affect the tatus light on the wi-fi card was wicd. when the card is in use the light is supposed to turn on, bu in any program other than the actual wicd gui the status light just stayed off.

---

### Post by casonar on 2008-03-26
I am having the same problem with -1% signal in wicd.  Here is my iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:173   Missed beacon:0

irda0     no wireless extensions.

```

---

### Post by casonar on 2008-03-26
Ok, I finally got connected wirelessly (I changed the wireless interface from wifi0 to wlan0 haha), but I am still getting -1% signal strength on the manager main window.  Although I am currently getting above 100% (such as 125% and 134%) strength when I hover over the icon in the system tray.

---

### Post by imdano on 2008-03-26
What's iwconfig look like when you're actually connected.  Sounds like your driver is doing something strange.

---

