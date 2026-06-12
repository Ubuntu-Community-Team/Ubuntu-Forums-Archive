---
title: "Wireless keeps disconnecting-connnecting in Feisty"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by fwallace99 on 2007-06-16
Hi all, I hope you can help me.

I have at home an Apple Airport, original model, which all my Macs running OS X can connect to fine. Also a FreeBSD laptop. Very easy and they work great. I also have a repeater in my living room so I can connect there as well (brick fireplace blocks the main signal otherwise).

HOWEVER, with Ubuntu 7.04 (I had no problems with Dapper Drake) I keep getting this problem:

Network applet will disconnect.
It will sometimes re-connect, sometimes not.

My thought was to do this "old school" by command line only, something like this:

sudo iwlist ath0 scanning
ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:74:82:F3
                    ESSID:"applenet"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:30:65:1C:B0:40
                    ESSID:"applenet"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
Then:

sudo iwconfig ath0 essid applenet mode Managed channel 1 ap 00:30:65:1C:B0:40

To get to the hardware address of the AP I want.

Then:

sudo iwconfig ath0 key open
sudo iwconfig ath0 key "mykey"

(Note, AP is WEP 128 bit only, not WPA).

BUT THEN, I can't seem to associate interface ath0 with a renewed DHCP session with the right access point. I'm also worried that the Network manager will kill my command line session as well.

Is this (Feisty dropping randomly wireless sessions) a problem with Feisty, or is it more related to my two AP in my WAN? Can I fix this with old-school command line fun? How can I set my interface with DHCP which I assume is the final old-school command line way?

Any help would be greatly appreciated. Thanks!

---

