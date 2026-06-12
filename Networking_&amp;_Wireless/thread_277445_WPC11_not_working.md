---
title: "WPC11 not working"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by kristopher_d on 2006-10-14
](*,) All right, I've been at this for 3 days (see rediculous).  When I installed Ubuntu I didn't have an internet connection so I didn't bother putting the wireless card in the slot (shouldn't need to at OS install any how).  Now I've got wireless broadband into my apartment, and Cat5 running from my Wireless modem to my laptop (absurd).

My WPC11 shows in device manager, and the output from iwconfig is 

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  ESSID:"ANY"
          Mode:Managed  Access Point: Not-Associated   Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


eth0 is my wired lan connection.
sit0 is unknown.

I have no clue where to go from here.  My router is on (not connected to the outside world yet, but on, and there are 2 other wireless networks available, but my most recent attempts have cause iwlist wlan0 scanning to return
> 
wlan0     Failed to read scan data : Operation not permitted


wlan0 doesn't even show network configuration.

Any guidance would be appreciated.]

---

### Post by gvgerman on 2006-10-14
You'll need to find out which chipset is in the WPC11.  Look here:  [Wireless Cards Supported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")  There are evidently 3 different chipsets used in the WPC11 depending on the version of the adaptor that you have. The solution is chipset dependent.  Once you know this, run some searches in the forums; there is quite a bit of information therein about WPC11.

More info is here:  [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Some more info is here:
[WiFi Troubleshooting]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting")

Re: wlan - my internal wireless adaptor and my card adaptor (if and when I use it) are shown as eth1 and eth2, respectively. There are some threads w/in the forum that talk about this but I don't have them handy and I don't recall the specifics as to why this is so.  The card does not necessarily need to be assigned to wlan to work.

Good luck ...

---

