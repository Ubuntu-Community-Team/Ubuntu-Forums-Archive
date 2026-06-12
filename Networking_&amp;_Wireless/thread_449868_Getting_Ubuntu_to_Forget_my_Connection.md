---
title: "Getting Ubuntu to Forget my Connection"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by SuperAndy on 2007-05-20
Hey, after trying many methods, i finally have ndiswrapper installed and working. As opposed to the fwcutter method, i think it is. Faster drivers, etc etc

But yea, when i try and connect to my network, with wpa protection, I am unable to connect. Network manager just says "attempting to join wireless network ntl", eventually reverting to my wired network.

I have wpa supplicant installed.

iwconfig returns the following:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:13 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and ndiswrapper -l returns the following:

```

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

```

I just want to try and get ubuntu to forget anything it knows about my ntl ssid, so i can try and start again. I dont get the option to type the wpa psk in, even though if i click another network in range, evenn if it is wpa personal, i still get a chance to enter the key.

i think if i can get ubuntu to forget this connection, i could be in with a shout.

Any help will be greatly recieved.

Andy

---

### Post by scrooge_74 on 2007-05-20
if you don't need that info you can open /etc/network/interfaces and delete the info pertaining to the conection for wlan0
if you want you can backup that file first

---

