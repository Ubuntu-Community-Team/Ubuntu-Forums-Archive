---
title: "[SOLVED] wlan with ovislink wl5400pcm"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by steffmeister on 2005-04-21
hi

just installed hoary hedgehog on my laptop some days ago...
and i tried to use my pcmcia wavelan ethernet card with... it was detected and is configured as eth1, i can set all settings in the gnome network settings, it even detects the available wavenets (don't know how you call this in english)...
it all seems great, but here are my problems:
* gnome-network-applet always shows 100% (which is definetly not true!)
* i don't get an IP over the DHCP
in windows i get an IP and approx. 60% to 70% signal strength...

any suggestions?

ps.: i'm sorry for my english...

---

### Post by spd106 on 2005-04-21
I'm not familar with your card, but have you tried looking at this howto in the wiki

[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto) 

It would be useful to post the message displayed by $iwconfig eth1 
and/or $iwlist eth1 scan


Hope this helps

---

### Post by steffmeister on 2005-04-22
hi

ok, i've read the wiki, but it wasn't really a help...

here's some output: 
$lscpi
0000:02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
0000:02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
0000:03:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

oke, first the two pcmcia interfaces, then my onboard ethernet controller and then my wlan card...


$iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"HTLWLAN"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:59:67:8D
          Bit Rate:5.5 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Link Quality=220/0  Signal level=-77 dBm  Noise level=-49 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:59:67:8D
                    ESSID:"HTLWLAN"
                    Mode:Master
                    Encryption key: on
                    Frequency:2.412 GHz (Channel 1)
                    Quality:219/0  Signal level:-78 dBm  Noise level:-41 dBm

hmm, why does it says here Mode:Master?

---

### Post by steffmeister on 2007-09-15
as this card works perfectly with current ubuntus... i mark this thread as closed...

---

