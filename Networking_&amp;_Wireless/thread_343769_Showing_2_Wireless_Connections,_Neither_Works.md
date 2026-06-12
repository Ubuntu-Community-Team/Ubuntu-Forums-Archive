---
title: "Showing 2 Wireless Connections, Neither Works"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Jack Of Clubs on 2007-01-22
I have Xubuntu 6.10 installed on my laptop (PII 366, 256 MB RAM) and I have a Cisco Systems Aironet 350 ethernet adapter.  When this card is in my computer, two wireless connections show up - one labeled eth1 and one labeled Wifi0 (eth0 is my regular wired connection, which works fine).

I don't know which one is the correct one or how to get rid of the other, and I can't get either one to make it connect to my WAP.  Can anyone shed some light on this?

---

### Post by Jack Of Clubs on 2007-01-22
Bump.

---

### Post by Mba7eth on 2007-01-22
Can show us the output of 
$iwlist
$iwconfig
please


Cheers,
      Mba7eth

---

### Post by Jack Of Clubs on 2007-01-23
Here is the output of iwlist:

```
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

```
Here is iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-92 dBm
          Rx invalid nwid:2267  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3479   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-92 dBm
          Rx invalid nwid:2267  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3479   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by Jack Of Clubs on 2007-01-23
Addendum: I don't know where the ESSID "tsunami" came from, but it's NOT the name of my wireless network.

---

### Post by Mba7eth on 2007-01-23
Please configer ur router to act as 802.11bg ( i don't know if that effet but just to be safe) 
and show us 
$iwlist eth1 scan

$iwlist wifi0 scan

this tsunami i think is the last wlan you got connected to with ur unbuntu.
And sorry for being late to reply:-\"

---

### Post by Jack Of Clubs on 2007-01-23
Whoa, the weirdest thing just happened.

On a whim, I went and turned off WEP and WPA on my router, and, lo and behold, my Xubuntu laptop can suddenly connect!

I guess I have to see if I can get it to work with security on, but at least it works now.

Mba7eth, I appreciate you taking the time to help. :)

Somehow my wireless is now eth0; I don't know why.  However, wired LAN still works also.

Well, now to try to configure a secure connection!  Wish me luck!

---

