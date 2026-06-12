---
title: "Access Point: Not-Associated when using netgear wg511 with ndiswrapper.  Help?"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by patchwolf on 2006-11-07
Hello,

New to Ubuntu and Linux in general.  Long-time Windows user, but have always valued the contributions the Linux community has put forward.

I wiped Windows off my Dell Inspiron 1150, and installed Dapper Drake three days ago.  For the most part I've had no major problems -- except for my wireless connection.

I've finally (after much reading and experimentation), been able to get my Netgear WG511 (v1) installed and detected by the O/S, but for some reasons I cannot get it to pick up my wireless router and complete the connection.

Some details:
* Router: Seimens SpeedStream6520
* Card: Netgear WG511 PCMCIA card.

Status lights on the card are: 1 solid green light, 1 black (non-lit) amber light.  When a connection is established, this light should engage.

iwconfig gives me this:

```

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"SpeedStream6520"
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=2 Mb/s   Tx-Power: 32 dBm
          RTS thr=2347 B  Fragment thr=2346 B
          Power Management:off
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0  invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed Bacon:0

```

I've already verified the Frequency and ensure that the card is using the correct WEP key, and so now I'm thinking that I need to fix that **Access Point: Not-Associated** bit before I can move on.

I've also noticed that if I boot the laptop with the card already inserted into the PCMCIA slot, then it doesn't pick it up at all; I have to bott, THEN insert the card for it to pick up the card's presence (based on the green light on the card.

Remember, I'm new to Unix in general.  Please be gentle.  I'm not scared of the command line (used to work on DOS, and BASIC before that), but I will need some more specific instructions than some others might.

---

### Post by vyktor69 on 2006-11-07
Try this. It's what worked for me.
goto:
/lib/modules/kernelversion/[kernel-version]/drivers/net/wireless and run:

sudo mv acx /root/ 
sudo depmod -a

Then reboot. ndiswrapper usually will work then.

---

