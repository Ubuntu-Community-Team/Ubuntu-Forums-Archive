---
title: "Problem with my wireless card"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by The_Swede78 on 2006-11-24
Hi guys!

I'm a newbie when it comes to linux so therefore I would like to apologize in advance for coming with stupid questions](*,) . My problem is the following:
I have an Acer 3000 with a wireless card that I just can't seem to work in Ubuntu (I have had Windows installed on the same computer with no problem whatsoever when it comes to wireless internetworking). When I look in the System - Administration - Networking meny the card actually shows up (does this mean that Ubuntu has found compatible drivers for it?). I have also installed all the wireless packages I could find like Kwifimanager and so on.   When I try to search for wireless networlks I end up with nada. I have no clue why. If there are some friendly souls out there willing to spread some light on my ignorance ;) I would be very grateful...

Best regards

Thomas

---

### Post by Tilex on 2006-11-24
What do you get as output when you type ```
iwconfig
```?

Also, in the System Settings -> Network Settings, is your wireless device enabled?  If you know the address of your router (eg. 192.168.1.1) try to add it in the "Routes" tab and click "Apply".  Does it help?

---

### Post by The_Swede78 on 2006-11-24
Hi Tilex, thanks for your reply. Yes, I have tries to enable the card and write the ssid of the network (an open school network), but it still did not work. I must say that I at this moment does not have access to a wireless network (although my neighbour does so I should be able to test it against his router:)  just to test if my card can autodetect the network).

The following information got back after executing the command iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"SU"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

