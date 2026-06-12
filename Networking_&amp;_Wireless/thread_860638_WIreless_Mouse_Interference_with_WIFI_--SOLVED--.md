---
title: "WIreless Mouse Interference with WIFI --SOLVED--"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by djarnold on 2008-07-15
Hello,

I have recently upgraded to 8.0.4(.1) and was able to connect to the internet with no problems using my Linksys rt2500 card.  However, there seems to be interference with my wireless Logitech G7 mouse (not really surprising since they are both in the 2.4 GHz range).  I also can hear some interference with my speakers (the sub sounds like someone is lightly blowing into the mic sometimes).   

The strange thing is that this same setup doesn't have the interference in Visa (I'm dual booting), or in Ubuntu 7.10 (I just upgraded).  I've tried setting default broadcast channels for my router (all 1-11) in hope of isolating the values with no change.  


Here's how I solved my problem:

Originally typing:
> 
~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"<YOUR ID HERE>"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <YOUR POINT HERE>   
          **Bit Rate=1 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=38/100  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 

By simply changing the Bit Rate=54 Mb/s the interference disappeared.  

> 
sudo iwconfig wlan0 rate 54M


To make this "Stick" see the thread [here]("http://ubuntuforums.org/showthread.php?t=764499&highlight=change+wireless+bit+rate")!

Hope this helps someone!

Cheers.

---

