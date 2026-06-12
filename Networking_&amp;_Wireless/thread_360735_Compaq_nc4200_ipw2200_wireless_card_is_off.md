---
title: "Compaq nc4200 ipw2200 wireless card is off"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by lotus49 on 2007-02-13
First of all, has anyone got this to work?  Just knowing it is possible would be a big help.

I have Ubuntu Edgy Eft installed on my Compag nc4200 which has an ipw2200 wireless card.

The card is recognised and the appropriate module loaded (see below) but I cannot see any wireless networks (nor, obviously, connect to them).

root@hummingbird:~# lsmod|grep ipw
ipw2200               115652  0 
ieee80211              35272  1 ipw2200

root@hummingbird:~# dmesg|grep ipw
[17179615.632000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179615.632000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179615.632000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179615.724000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17179616.336000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)

I suspect the first line in the iwconfig output below points to the real problem (but I cannot be sure).

root@hummingbird:~# iwconfig eth1
eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Does anyone know how to turn the radio on?  (Just in case anyone is thinking of suggesting pressing the wireless on/off switch, I've thought of that - I'm not that daft).

Any suggestions or ideas?

---

### Post by IMELucky on 2007-02-13
My HP Compaq has this exact same wireless card and it does work so I know that it is possible to get yours working too. However, in my case it was automatically detected and I just needed to install the gnome network manager applet and it works great.

Anyway, try doing just "iwconfig" and make sure the eth1 is in fact your wireless card. Mine looks like this:

imelucky@imelucky-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth3      IEEE 802.11g  ESSID:"StoutAirportNetwork"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:A9:6A:69:90   
          Bit Rate:12 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-57 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:56   Missed beacon:11

sit0      no wireless extensions.

Good luck

---

### Post by lotus49 on 2007-02-13
I had already checked by just running iwconfig with no options but I didn't want to clutter my post.

Which laptop do you have?  Does it have a software controlled kill switch for the wireless card (I strongly suspect that this is the culprit)?

---

### Post by IMELucky on 2007-02-13
I have a hardwire switch, but I can turn off the network adapter through the network manager applet (or in Windows, by right clicking on the wireless monitor in the system tray)

However, right now Ubuntu doesn't come with network manager package, so check system-->administration-->networking to see if its disabled in there.

Also, did you try passing the essid and network key (if you have on) directly to iwconfig?

example:
iwconfig eth1 essid "FARVA320" key "579055eaf1"

---

### Post by lotus49 on 2007-02-28
Thanks for your help and, although I had already tried it, installing network-manager-gnome was the solution for me.

I must have made some screw up with the configuration, so I reinstalled from scratch and then installed network-manager-gnome and this time it worked fine.  I clicked in the icon, it brought up the list of wireless networks it could see, I typed in my WPA passphrase and now it works fine.

By creating a file /etc/modprobe.d/ipw2200 with the single line "options ipw2200 led=1" I managed to get the blue LED to work as well.

I must have managed to make some configuration mistake prior to installing network-manager-gnome so when I did later install it it didn't work.

My nc4200 now runs Ubuntu really well.  I haven't tested the pcmcia slot, bluetooth or IR but everything else works fine.  I can even turn the wireless card on and off using the switch just like I used to be able to in XP.

---

