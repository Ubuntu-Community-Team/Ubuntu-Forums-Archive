---
title: "belkin usb adaptor not associated to access point!"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by gouche on 2007-04-01
Hey everyone.

Been trying to get my Belkin Wireless USB Adaptor to work in Edgy for the past week or so. Thought I had it when I installed the driver via ndiswrapper, the device appears in Networking and I can see my access point when I use ```
iwlist wlan0 scanning.
``` However iwconfig tells me that it's not associated with any access point and gives no ESSID even though I have manually assigned these through iwconfig myself! 
Here's the output of iwconfig.
```
gouche@ubuntu:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

 If someone could help me out I'd be very grateful!
If there's any other info you need just ask, I'll try my best but this is a learning experience for me!

---

### Post by gouche on 2007-04-02
*bump*

---

### Post by bodycoach2 on 2007-04-02
What result do you get when you type:

lsusb

in terminal?

---

### Post by gouche on 2007-04-02
Cheers for the reply. 

The device shows up in lsusb:
```
gouche@ubuntu:~$ lsusb
Bus 004 Device 002: ID 050d:7051 Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
gouche@ubuntu:~$ 
```

---

### Post by bodycoach2 on 2007-04-02
Here's a couple of threads that might help:

[http://ubuntuforums.org/showthread.php?t=304181&highlight=belkin+7051]("http://ubuntuforums.org/showthread.php?t=304181&highlight=belkin+7051")
[URL="http://ubuntuforums.org/showthread.php?t=361287&highlight=belkin+7051"]
http://ubuntuforums.org/showthread.php?t=361287&highlight=belkin+7051[/URL]

See if any of those might apply.

---

### Post by gouche on 2007-04-02
Thanks for the help bodycoach2 but I got it working.

I had set the ESSID and key, but I had made a stupid typo which I've only just discovered! I feel like an idiot!

---

