---
title: "Wireless WPA Steps - Completely New"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by FrozenPixel on 2006-10-30
Hello,

Firstly I'd like to say I cannot believe all these years I have been missing on an operating system so robust as ubuntu. Thanks so much to everyone for all their efforts, I'm simply in awe.

This is my very first install of linux and although I"m dual booting with my WinXP OS, I'm looking forward to learning curve.

I have installed ubuntu on a partition on my laptop that runs a Dlink DWL-650G wireless card but I am very unclear about something called the WPA_Supplicant. So far I ran the command 'iwconfig' and it produced this information so I take it, right off the shelf my card is recognized.

Terminal Info:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:2  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now I have went into the Network interface but my WPA key is too long for that particular application, do I enter the key somewhere else to get the connection to work? I'm using WPA - TKIP - PSK.

I have no real terminal experience but I am quite capable when pointed in the right direction but this is new so hopefully you will put up my newbie questions. I did a search on the WPA Supplicant but most of the threads have been beyond my knowledge to even know or where to find the file to edit, if need be.

Thanks and any help would be greatly appreciated.

---

### Post by thoolihan on 2006-11-01
I don't know how exactly to do it, but I know you use wpa supplicant:

I'd try the following and then google for some guides on them:

sudo apt-get install wpasupplicant wpagui

---

