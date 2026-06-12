---
title: "Need help with installing Ralink MT7610U wireless driver"
date: 2017-12-10
forum: Networking &amp; Wireless
---

### Post by stratovarios on 2017-12-10
hi guys:
after installing my tp link archer t2UH, CHIPSET= MediaTek MT7610U on
ubuntu 14.04 trusty tahr 32bit, im newbie on linux ubuntu live usb.
by instructions of salmorgeek
"[https://salmorejogeek.com/2015/08/18/tp-link-ac600-archer-t2uh-funcionando-en-linux-impossible-is-nothing/](https://salmorejogeek.com/2015/08/18/tp-link-ac600-archer-t2uh-funcionando-en-linux-impossible-is-nothing/)"
i see that my usb adpter hasnot a chipset name or/is unknown chipset :
root@ubuntu:/home/ubuntu# airmon-ng start ra0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
2246    avahi-daemon
2247    avahi-daemon
2994    wpa_supplicant
7745    NetworkManager


Interface    Chipset        Driver

wlan0        Atheros     ath9k - [phy1]
ra0        Unknown     usb - [phy0]mon0: ERROR while getting interface
flags: No such device
                (monitor mode enabled on mon0)
when i use: iwconfig
ra0       Ralink STA  ESSID:""  Nickname:"MT7610U_STA"
          Mode:Monitor  Frequency=2.427 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

when i use:
root@ubuntu:/home/ubuntu# sudo iwlist ra0 scan
ra0       Interface doesn't support scanning : Invalid argument

when i use:
root@ubuntu:/home/ubuntu# modprobe MT7610U_STA
modprobe: FATAL: Module MT7610U_STA not found.
finally; when i use:
root@ubuntu:/home/ubuntu# sudo ifup ra0
Ignoring unknown interface ra0=ra0.
    It's not recognized when I plug it and unplug it. What could be
the problem & what i have forgotten during instqllqtion stages?
thanks a lot

---

