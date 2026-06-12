---
title: "Wifi slooooooooooooooooow"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by bigzak on 2005-04-17
Hi all,

I've just set up a small wireless LAN so I can browse from anywhere in my house, and it consists of one DWL-1000 access point hooked up to my router, and one DWL-650+ wifi card (22Mb/s apparently) which uses the acx100 chipset.

All is well... ish. The card connects, I can browse, and things seem to work (I'm using said connection right now to type this). However, there seems to be some issues in data transfer. Sometimes, nothing seems to go down the pipe at all, then a whole lot will happen in a small burst. I keep having to kill and restart connection attempts (e.g. when browsing, stop and reload the page, or when streaming, stop and start the track).

I've looked at iwconfig, and I get this:

```

wlan0     IEEE 802.11b+  ESSID:"SPIFFYWLAN"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.437 GHz  Access Point: 00:40:05:AE:FF:EF
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:70/100  Signal level:62/100  Noise level:1/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:0   Missed beacon:0

```

Seems fine, except that the signal level is 62% (I'm literally 8 feet away from the access point in an otherwise empty space) and the link quality is 70%. Notice also that the bit rate is only 1Mb/s!!

If I try to change the bit rate to 11Mb/s with:

```
sudo iwconfig wlan0 rate 11M
```

then no data is ever transferred. If I set it to auto then it goes back to 1MB/s.

If there are any suggestions, I will try anything to get this thing to work better. Sometimes it's absolutely fine and I browse away from the lounge or kitchen (the AP is upstairs), but at other times (like right now) I can't get a good connection for love nor money. Incidentally, I am not sure but I think I only get 1Mb/s even on a good day, and even then I get some 'sticky' connections that seem to cause all other connections to just stop in their tracks.

---

### Post by jshein on 2005-04-17
First

use wavemon in a console to determine your actual signal / noise ratio & link quality

Depending on what card you are using, install & run kismet and see if there are any neighbors who have wireless that may be interfering with your signal.

Essentially there are only 3 non-overlapping channels in 802.11b/g
1,6,11

Thats it. If anyone in your area is running on the same or overlapping channel, then your performance will suffer dramatically.

IE: you are running on CH6, 1 neighbour is running on CH4 and another on CH 6 you will lose 70% or more of your link transfer rate. Most routers default to CH6. 

If you can't install / run kismet, then change to an alternate channel and see if that helps.

---

