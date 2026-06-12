---
title: "Settings not 'sticking' and connection dropping"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-16
I seem now to be able to periodically get my wireless network working, but still have two significant problems: -

1. When I reboot I lose everything, despite everything seeming correct in /etc/network/interfaces and ndiswrapper being loaded in /etc/modules.

2. The wireless network drops a lot, particularly during downloads and when it does I have to mess about (literally trying them in different orders) to get stuff working again: -

sudo ifdown wlan0
sudo iwconfig wlan0 ap <my_router_address>
sudo iwlist wlan0 scan
sudo ifup wlan0

There's no pattern to what fixes it - sometimes ifdown/ifup works, sometimes I have to reconfigure, sometimes I have to even respecify the essid, and sometimes it just doesn't come back up at all.

One thing I have noticed is if I am doing a large number of downloads and I try to do something else network related (e.g. open a web page), it dies straight away.

Anybody give me some indicators on what to look at for a) the dropping and b) the lack of permanency of my settings?

---

### Post by Floppyjoe on 2007-02-16
When your connection drops out, if you enter the command:
```
ifconfig
```
Does it show that you still have an IP address for your wireless adapter?

---

### Post by wej1971 on 2007-02-16
I'll check next time I get it booted up. Unfortunately the g/f's in Windows on it atm!

---

### Post by wej1971 on 2007-02-17
No, when I start downloading something it downloads for a while and then stops.

When I do ifconfig wlan0 immediately after this happens, the Ip address has vanished.

This coupled with the fact that it appears to be hit and miss whether the connection works in the first place (I have to keep taking the interface up and down and scanning) makes me wonder whether to switch to a linux with better hardware support (e.g. freespire) or abandon linux altogether :(

Anyone got any last ideas before I give up completely - I've been at this over a week now.

---

