---
title: "hostap driver in master mode help?"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by enigma_0Z on 2006-12-28
I'm trying to get a prisim pcmcia card (specifically the old D-Link DWL-650) to run in master mode and act as an AP.

When I try to put the card in master mode with

```

iwconfig wlan0 mode master

```

it switches properly, but iwconfig says:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      no wireless extensions.

sit0      no wireless extensions.

wifi0_ifrename  IEEE 802.11b  ESSID:"test"
          Mode:Master  Access Point: Not-Associated   Bit Rate:11 Mb/s
          Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"test"
          Mode:Master  Access Point: Not-Associated   Bit Rate:11 Mb/s
          Sensitivity=1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The thing that I see is "Access Point: Not-Associated". Is there some other option that I need to get an AP ID?

---

