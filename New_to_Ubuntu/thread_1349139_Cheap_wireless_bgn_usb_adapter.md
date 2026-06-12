---
title: "Cheap wireless b/g/n usb adapter"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by anewguy on 2009-12-07
I was at our local Micro Center store today, and they had Tenda brand model W311U USB wireless b/g/n adapters on sale for $14.99, so I picked one up.  It seems to work out of the box - though I have to say that with some caveats:  there are no wireless networks for me to connect to here, but when the adapter is plugged in to a USB port, network manager adds the "wireless connections" section but shows as disconnected (assuming therefore that the adapter is working but no wireless networks for me to connect to - go figure - I'm in a *BASEMENT* apartment!).  I think it is using one of the built in ralink drivers.  A iwconfig with the adapter plugged in shows:

dave@dave-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

wmaster0  no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dave@dave-desktop:~$ 


Which I take it to mean that wlan3 is active (shows as bgn) just not connected to anything.

So, *if* I'm correct in assuming it's working out of the box, this could be an inexpensive way for someone looking for a wireless adapter.

Just thought I'd pass it along, and hopefully I'm correct in it is actually working.

Dave :)

---

### Post by ikt on 2009-12-08
Heya,

If you can you should add it to this page:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters)

Cheers :)

---

