---
title: "No automatic start of rt2500 WLAN"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by Donalbain on 2005-07-02
Hi! 
 
 I have to use WLAN all the time, so it bothers me that starting my Ubuntu Hoary often (but not always) does not also initialize the ra0-interface. Most times I have to start RaConfig2500 and/or try restarting the network device (ifup/ifdown ra0), until it works. Some lucky days, it works without interference, so my setup can not be completely wrong. 
 
 I also suspect that loading the rt2500-module does not trigger loading the 
 /etc/Wireless/RT2500STA/RT2500STA.dat-file. After loading the module, iwconfig still shows no wireless extensions. Is that normal? I suspected that it would at least display the ESSID. But when I modify my setup by using RaConfig2500, the changes are automatically written to that file. I don't understand that. 
 
 In another post, someone wrote, this was caused by not editing the templete with vi -b. After reading, I setup a whole new /etc/Wireless/RT2500STA/RT2500STA.dat from the tarball with the same result. 
 
 Do you have any suggestions where to look? 
 
 (Version of the driver package: 1.4.6.1, kernel 2.6.10-5-k7, Ubuntu Hoary) 
 
 Donalbain

---

### Post by fluideye on 2005-07-02
Not sure if it works in Gnome but KWiFiManager is in the repositories and works well for me.

# sudo apt-get install kwifimanager

Here's a link to how I set up my card initially

[http://fluideye.com/blog/2005/05/26/howto-rt2500wireless-card/](http://fluideye.com/blog/2005/05/26/howto-rt2500wireless-card/)

---

