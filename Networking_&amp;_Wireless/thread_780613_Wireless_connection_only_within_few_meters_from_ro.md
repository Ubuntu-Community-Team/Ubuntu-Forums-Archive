---
title: "Wireless connection: only within few meters from router (and slow) - Broadcom card"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by DoubleU29 on 2008-05-03
Hello, I've recently installed ubuntu (8.04 hardy) for the first time, I'm almost new to linux. 
I experience a strange problem with my wireless connection, I have a Broadcom (bcm4312 rev01, or 4311) card on my Hp pavilion dv6000 laptop, i followed the procedure to install the firmware (b43-fwcutter) and then i installed the drivers (b43). 
I was happy when it started working immediately...

Problem is: the connection is already slow when i am a few centimeters from my router, but stops working when i go a bit further (next room or corridor).
I  think the card is correctly detected because it works...
I've noticed that clicking with the right button on the network icon on the top right corner and then clicking "Connection Information" tells me:

Interface: wlan0
Speed: 1 Mb/s (or 2 Mb/s)
Driver:  

The speed is incredibly slow and the driver is blank.

I've tried removing the WPA protection but the problem remained unchanged.

This is what iwconfig gives me:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"RT2561"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:F6:26:20:A1   
          Bit Rate=12 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=93/100  Signal level=-41 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



What other command could be useful to you?

I've tried sudo iwconfig wlan0 54M, as suggested in some post but it says iwconfig: unknown command "54M".

I've tried to install b43legacy but nothing.

Please help, without wireless I'll have to go back to windows!
Thanks!

---

### Post by Ayuthia on 2008-05-03
> **DoubleU29 said:**
> I've tried sudo iwconfig wlan0 54M, as suggested in some post but it says iwconfig: unknown command "54M".
You might try:
```
sudo iwconfig wlan0 rate 54M
```
Not for sure if it helps, but if for some reason, you are not satisfied, you can try the NDISwrapper route: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps!

---

### Post by DoubleU29 on 2008-05-04
I've solved the problem with this workaround: 

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

which is the based on the one you suggested me with some differences in the end. 
Now it works perfectly.
Thanks!

---

