---
title: "Can't change wifi config with iwconfig"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by marion on 2005-08-27
I'm trying to set my essid and set the mode as well.  This is the output from iwconfig:

iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I set the essid via the networking gui, but it's not reading it.  I'm on an open access point as well, so the mode shouldn't be managed.  In FC4 I could set the mode to auto and it worked fine, but I can't get any of the changes to stay.

---

### Post by Qylvaran on 2005-08-28
Did you use 'sudo' in front of 'iwconfig'?  You need to be root to change the settings.  Also, if you don't use 'sudo iwconfig' to display info on your connection, it leaves some things out.

If you already used the command 'sudo iwconfig wlan0 mode auto' to change the mode, then I can't help any further.  I just figured my wireless settings out myself (and your post indirectly helped.  Thank you).

---

### Post by gravestone on 2005-08-29
Some of the wlan drivers don't work with any. You have to manually set the essid.

sudo iwconfig wlan0 essid mynet

I usually configure mine on the command line with a script, because my laptop has built in wire and wireless, and the wireless requires the key as well.

---

