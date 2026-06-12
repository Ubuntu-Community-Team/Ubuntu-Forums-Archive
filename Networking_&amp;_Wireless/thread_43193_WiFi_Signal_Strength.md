---
title: "WiFi Signal Strength"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by stevenyu on 2005-06-21
Hi guys, I am trying to get the Gnome Panel Applets **Network Connection Status** to display the correct signal strength of my Netgear WG311v2 via NDISWRAPPER

under /proc/net/wireless

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 17
 wlan0: 0000  100   195     0        0      0      0      0      0        0


However that is not right, as quality is always 100, and no noise (I wish)

The correct stats can be found under /proc/net/ndiswrapper/wlan0/stats

signal_level=-61 dBm
tx_frames=14810332926478123008
tx_multicast_frames=13842368857572425728
tx_failed=14810332517382485968
tx_retry=14810333029557338208
tx_multi_rerty=2777772901616
tx_rtss_success=13840451622601934064
tx_rtss_fail=3239660960
ack_fail=13847096542614867360
frame_duplicates=0
rx_frames=13840452319457575120
rx_multicast_frames=13847099428815711273
fcs_errors=7518995696

is there anyway I can some how convert the stats from ndiswrapper to the standard WiFi stats as shown in the /proc/stat/wireless

:smile:

---

### Post by Zelut on 2005-06-21
As far as I understood that still wasn't an option.  I noticed that my signal strength was always 100% (which I knew wasn't true) but as far as I've read there isn't much we can do about it.  The way I see it we did a hack using ndiswrapper so I'm content with even getting it to work at all :)

I guess if you REALLY want to you could check out the code for the gnome applet & see where it finds the signal strength.  You could attempt a second hack to have it call the info you've posted above... would definitely take some coding skill though.

---

